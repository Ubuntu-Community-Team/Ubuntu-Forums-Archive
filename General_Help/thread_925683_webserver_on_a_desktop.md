---
title: "webserver on a desktop"
date: 2008-09-20
forum: General Help
---

### Post by haroldh7 on 2008-09-20
I once got help with links before here and have lost them.
I now ask again for help with installing a home webserver on a ubuntu desktop with a blog.
I do hope someone can help me with the links or information on what files that will be needed to do this.

I do hope someone can help.

Thanks
Harold

My system:
Ubuntu OS
Desktop computer, 550 mhz cpu, 256 megs ram.
20 gig hard drive
internet connection with dsl.

---

### Post by mb_webguy on 2008-09-20
Well, first of all, you'll need Apache and probably PHP, so you might as well go with a full LAMP setup (which will also get you MySQL).  Open Synaptic and go to Edit->Mark Packages By Task and select "LAMP Server", then apply the changes.

The default web root (i.e. where your html files go) is the /var/www directory.

I don't know of any blog systems off hand, but I'll check...

EDIT:  You might want to check the list on [this page]("http://en.wikipedia.org/wiki/Blog_hosting_service").

---

### Post by cariboo on 2008-09-20
IF you want to install the complete lamp server package, go to System-->Administration-->Synaptic Package Manager-->Edit-->M<ark Packages By Task and select Lamp server in the window that pops up.

This will install and configure Apache2, Php5, and Mysql. THis will be enough to allow you to install the blogging software you want. If you search for blog in Synaptic it will show you several blogging software packages.

Jim

---

### Post by haroldh7 on 2008-09-21
I now have the lamp installed.
I now wonder, do I configure the apps in GUI or command line to run the way it should be or what..

What about this file called phpmyadmin, do I need it or not.
Do I need to make any changes with apache or the database app or not..
If so where do I find the configuration file for it.

Thanks

---

### Post by Cool Surfer on 2008-09-21
yes you might need phpmyadmin, if you want to play with your mysql databases. But generally it is best left to the experts to do that.

---

### Post by Cool Surfer on 2008-09-21
no harm, go and install phpmyadmin ... :)

---

### Post by fragos on 2008-09-21
The LAMP install requires a bit of configuration to run PHP code. The file to be edited is /etc/apache2/httpd.conf. If it's already there it's probably empty, if not create it. Place the following three lines in it. The

LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

The web server will have to restart for the configuration changes to take effect. The next time your sytem boots will do that or run the following CLI.

sudo /etc/init.d/apache2 restart

---

### Post by mb_webguy on 2008-09-22
AFAIK, PHP with the LAMP installation works out of the box.  If not, you should just be able to type "sudo apt-get install libapache2-mod-php5" to enable PHP support.

I didn't use the LAMP install because I didn't initially need MySQL, so I just installed the Apache and PHP packages.  I ran a phpinfo script immediately after installation, and it worked just fine.  I believe the LAMP installation installs the same packages, so you shouldn't have to edit any configuration files to get things working.

---

### Post by fragos on 2008-09-22
My statement matches my actual experience Installing with Synaptic by marking the LAMP task on Ubuntu 7.10 and 8.04.

---

### Post by mb_webguy on 2008-09-22
*nod*  As I said, I didn't install LAMP using the task selection.  And I wasn't saying you were wrong -- only that I hadn't needed to do any manual configuration.

However, I stand by my statement that the libapache2-mod-php5 package does the configuration for you -- it just uses the /etc/apache2/mods-available/php.conf file rather than adding the LoadModule and AddType lines to the httpd.conf file, which is arguably the better (if not necessarily the simpler) way of doing it.  That's why I suggested installing that package if installing LAMP by the task selection method didn't do the configuration for you.

---

