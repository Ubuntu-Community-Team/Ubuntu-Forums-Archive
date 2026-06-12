---
title: "Apache2 +PHP5"
date: 2008-08-26
forum: General Help
---

### Post by tomehb on 2008-08-26
Ubuntu 8.04

Mods: Feel free to move this post, i'm not to sure where to post such item.

Ok, i dont see where i have gone wrong.. but i failed. I guess mainly because the first time i screwed it up every other attempt has failed. Basically i have installed Appache2, all working fine. Came to install php5 and i just use  sudo apt-get install php5 libapache2-mod-php5.

After this i restart apache2... 

And then i try to use a php file and firefrox asks if i wish to download it. What do i need to configure? I had a look in /etc/apache2/httpd.conf and its empty any reason why?

Any help would be good or links.  Could not find any simple guides on the net that worked.... :(*

Someone point me in the correct direction please

Thanks.

---

### Post by Sycron on 2008-08-26
Take a look here:[http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100](http://joeabiraad.com/linuxunix/installing-lamp-on-ubuntu-710-linuxapachemysqlphp/100)

---

### Post by Bliepo32 on 2008-08-26
Well, if I were in your situation, I would open synaptic and search for Apache and php, and completly remove them (back-up files you wish to keep!).

Then, install Apache and php by typing

```
sudo apt-get install apache2 libapache2-mod-php5
```

---

### Post by mbeach on 2008-08-26
httpd is empty because:
```

      1 # This is here for backwards compatability reasons and to support
      2 #  installing 3rd party modules directly via apxs2, rather than
      3 #  through the /etc/apache2/mods-{available,enabled} mechanism.

```
use /etc/apache2/apache2.conf and the other .conf files.

change the ownership of the php file that doesn't work correctly.

let's assume its called /var/www/myphpfile.php

```
sudo chown www-data:www-data /var/www/myphpfile.php
```

and see if that makes a difference when you try to view it in the browser.

---

### Post by tomehb on 2008-08-27
> **Bliepo32 said:**
> Well, if I were in your situation, I would open synaptic and search for Apache and php, and completly remove them (back-up files you wish to keep!).

Then, install Apache and php by typing

```
sudo apt-get install apache2 libapache2-mod-php5
```

Sigh,

i did this still not working :(

---

### Post by nbayiha on 2008-08-27
You just have to go to firefox tools and clear private data and everything should be fine.:lolflag: I had the same problem. You set everything nicely but you forget to clear up the old Cache and that's the problem.

---

### Post by fragos on 2008-08-27
edit httpd.conf

Search inside the file for "LoadModule rewrite_module lib"(hit ctrl + f to search).

Underneath this line type: LoadModule php5_module /usr/lib/apache2/libphp5.so

The directories above just happens to be were my "libphp5.so" file happens to be for me. Type in console: locate libphp5.so

That will tell you were your libphp5.so file is.

Now search the file (ctrl +f) for "AddType application/x-gzip"
Underneath this line add the following two lines:

AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

Save httpd.conf

Now go back into console and type: apachectl start
or sudo /etc/init.d/apache2 restart

PHP and Apache should now be working.

Also check [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by mbeach on 2008-08-29
fragos, once installed from synaptic I believe that its no longer in httpd.conf

use 
/etc/apache2/mods-available/php5.conf
/etc/apache2/mods-available/php5.load

use "sudo a2enmod php5" to enable

---

### Post by fragos on 2008-08-29
I can only speak to what I did to get PHP working with my web server. FYI apache2.conf expects to find user configuration commands in httpd.conf. This differs from Apache 1. I installed Apache2, PHP and MySQL as by installing by task in Synaptic LAMP.

---

### Post by SpazDes on 2008-08-30
Hi I seem to be having the same problem as the other guy/gal. I'm not sure why but I am.

> **Bliepo32 said:**
> Well, if I were in your situation, I would open synaptic and search for Apache and php, and completly remove them (back-up files you wish to keep!).

Then, install Apache and php by typing

```
sudo apt-get install apache2 libapache2-mod-php5
```

I tried this to get my php working again and it did not work for me.

> **mbeach said:**
> httpd is empty because:
```

      1 # This is here for backwards compatability reasons and to support
      2 #  installing 3rd party modules directly via apxs2, rather than
      3 #  through the /etc/apache2/mods-{available,enabled} mechanism.

```
use /etc/apache2/apache2.conf and the other .conf files.

change the ownership of the php file that doesn't work correctly.

let's assume its called /var/www/myphpfile.php

```
sudo chown www-data:www-data /var/www/myphpfile.php
```

and see if that makes a difference when you try to view it in the browser.

I tried this to get php working, but it did not work for me.


> **nbayiha said:**
> You just have to go to firefox tools and clear private data and everything should be fine.:lolflag: I had the same problem. You set everything nicely but you forget to clear up the old Cache and that's the problem.

I tried this and it didn't work for me either.. :(

Does anyone have any other ideas?

I tried modding the httpd.conf, but it was empty upon opening. :(

---

### Post by fragos on 2008-08-30
httpd.conf is empty on install because it is where the user is suposed to make configuration changes rather than in apache2.conf which has an include statemet for httpd.conf.

---

### Post by SpazDes on 2008-08-30
Well I added the following to httpd.conf

AddType application/x-httpd-php .php .phtml
AddType application/x-httpd-php-source .phps

And I restarted apache and still nothing, everytime I access my localhost it requires me to download the php/phtml file.

---

### Post by fragos on 2008-08-30
I wish I could help but my experience with Apache is limited. Perhaps by installing LAMP with synaptic did some configuration that wasn't automatic when the components are installed separately. When I was running Ubuntu 7.10 the configuration I suggested worked. When I did a clean install of Ubuntu 8.04 and LAMP I used the httpd.conf I created for 7.10. Apache isn't easy to set up.

---

### Post by agentfusion on 2010-10-21
> **tomehb said:**
> Ubuntu 8.04

Mods: Feel free to move this post, i'm not to sure where to post such item.

Ok, i dont see where i have gone wrong.. but i failed. I guess mainly because the first time i screwed it up every other attempt has failed. Basically i have installed Appache2, all working fine. Came to install php5 and i just use  sudo apt-get install php5 libapache2-mod-php5.

After this i restart apache2... 

And then i try to use a php file and firefrox asks if i wish to download it. What do i need to configure? I had a look in /etc/apache2/httpd.conf and its empty any reason why?

Any help would be good or links.  Could not find any simple guides on the net that worked.... :(*

Someone point me in the correct direction please

Thanks.


I know this is resurrecting a really old thread. but I ran into the same problem with a fresh install of lucid for my web server after a hard disk failure and subsequent installation of a new physical disk.

Here's how I solved the problem:

1) ```
sudo cp /etc/apache2/mods-available/php5.conf ~/php5.conf
```2) ```
sudo nano(gedit,kate,etc) /etc/apache2/mods-available/php5.conf
```3) Under

 ```
<FilesMatch "\.phps$">
        SetHandler application/x-httpd-php-source
    </FilesMatch>

```add the following 

    ```
<FilesMatch "\.php4">
        SetHandler application/x-httpd-php
    </FilesMatch>
    <FilesMatch "\.php5">
```4) Save and close the file.

5) ```
sudo apache2ctl stop
```6) ```
sudo apache2ctl start
```*Et voila*.  That's it.

---

