CKEditor Drupal Feature
=======================

This is a simple feature wich contains a functioning CKEditor installation (using the CKEditor module).

It sets up a new *"ckeditor"* text format. Using it you got a correctly set up CKEditor on your textarea with not too much and not too small buttons. 

It also lets you add `.img-right`, `.img-left` or `.img-mid` class to your inline images (using the "Style" dropdown). So you can set these in your theme's stylesheet. (The editor is set to use the *style.css* of your Drupal theme instead of the default stylesheet of CKE.)

(This feature is tested with 3.6.x versions of CKE but not with 4.x versions.)

HOWTO USE
---------

### Make a new Drupal installation with CKEditor feature:
img
* `drush make https://raw.github.com/tanarurkerem/tanarurkerem_ckeditor/master/tanarurkerem_ckeditor.make [WEBDIR]`
* Install Drupal (`drush si [YOUR OPTIONS]`)
* Enable Features module (`drush en -y features`)
* Enable Tanarurkerem CKEditor feature at admin/structure/features (`drush en -y tanarurkerem_ckeditor`)
* Revert Tanarurkerem CKEditor settings (`drush fr -y tanarurkerem_ckeditor`)

### Install Tanarurkerem CKEditor feature to an existing site

* `drush make --no-core --tar https://github.com/tanarurkerem/tanarurkerem_ckeditor/raw/master/tanarurkerem_ckeditor.make tanarurkerem_ckeditor`
* Mac OSX - bsdtar 2.8.3 - libarchive 2.8.3

 `tar -x -s /tanarurkerem_ckeditor// -C [YOUR DRUPAL WEB DIR] < tanarurkerem_ckeditor.tar.gz` 
 
* Ubuntu - (GNU tar) 1.25

 `tar -x -z --xform s/tanarurkerem_ckeditor// -C [YOUR DRUPAL WEB DIR] < ./tanarurkerem_ckeditor.tar.gz`

### Use it in a .make file

* add the following lines to your make file:

```
projects[features][subdir] = "contrib"
projects[ckeditor][subdir] = "contrib"

libraries[ckeditor][download][type] = "file"
libraries[ckeditor][download][url] = "http://download.cksource.com/CKEditor/CKEditor/CKEditor%203.6.2/ckeditor_3.6.4.tar.gz"

projects[tanarurkerem_ckeditor][type] = module
projects[tanarurkerem_ckeditor][subdir] = features
projects[tanarurkerem_ckeditor][download][type] = git 
projects[tanarurkerem_ckeditor][download][url] = git://github.com/tanarurkerem/tanarurkerem_ckeditor.git  
```