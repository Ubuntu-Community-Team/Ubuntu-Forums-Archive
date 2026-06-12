---
title: "[SOLVED] installing drupal cms !!!!!!!!!!"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by chinmaya_n on 2008-12-22
[B]I am new to drupal. I dont know how to install it so i searched for a clear installtion procedure. But none of the sites i searched were fruitfull....:(

Its all a mess to install Mysql,php etc.. I know they are prerequisites to for installing drupal.None of the sites i found are clear to me...:confused:

Can anyone please tell me a link. How to install it. I would like to learn it as early as possible.....!![/B]

---

### Post by namdung on 2008-12-22
> **chinmaya_n said:**
> [B]I am new to drupal. I dont know how to install it so i searched for a clear installtion procedure. But none of the sites i searched were fruitfull....:(

Its all a mess to install Mysql,php etc.. I know they are prerequisites to for installing drupal.None of the sites i found are clear to me...:confused:

Can anyone please tell me a link. How to install it. I would like to learn it as early as possible.....!![/B]

I guess you are having issues installing LAMP. In Synaptic Package Manager, search and install the following:
    * apache2
    * php5-mysql
    * libapache2-mod-php5
    * mysql-server

[http://fosswire.com/2007/05/29/installing-and-configuring-lamp-on-ubuntu-part-1/](http://fosswire.com/2007/05/29/installing-and-configuring-lamp-on-ubuntu-part-1/) 

Test to see you php file is working properly. Copy the drupal folder or symbolic link to the /var/www/ folder.

In a web browser type [http://localhost/drupal](http://localhost/drupal) (assuming drupal is the folder copied to www folder). Follow instructions to install drupal.

Good luck.

---

