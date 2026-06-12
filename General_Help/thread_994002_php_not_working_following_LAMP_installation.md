---
title: "php not working following LAMP installation"
date: 2008-11-26
forum: General Help
---

### Post by webmonkey47 on 2008-11-26
Hi to you all, 
I'm fairly new to Ubuntu and loving it, however, spent all afternoon getting nowhere with this problem.

I've been trying to set up a LAMP environment on 8.10 desktop using a variety of apt-get and Synaptic methods and finally tried this process:

1. sudo apt-get install apache2 php5 php5-cli php5-mysql mysql-server mysql-client
2. sudo apt-get install php5-gd php5-curl php5-sqlite php-pear smarty
3. sudo apt-get install subversion
4. echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn
5. sudo a2enmod userdir
6. sudo a2enmod rewrite
7. sudo /etc/init.d/apache2 force-reload

which I got from this website: [http://justinsomnia.org/2008/09/setting-up-a-nice-lamp-environment-on-ubuntu/](http://justinsomnia.org/2008/09/setting-up-a-nice-lamp-environment-on-ubuntu/)

but I cannot get php to work.. tried testing using [<?php phpinfo(); ?>] but keeps prompting me to download phptest.php instead of running it.

Really appreciate being pointed in the right direction to fix this.. a step by step solution would be even better :)

---

### Post by mbeach on 2008-11-26
from: [http://ubuntuforums.org/showthread.php?t=979567](http://ubuntuforums.org/showthread.php?t=979567)

could also try:
sudo apt-get install php5 libapache2-mod-php5

---

### Post by Peter09 on 2008-11-26
PHP by default does not provide command line support. It is setup to be run from apache.

You need to download the cli.

```
sudo apt-get install php5-cli
```

---

### Post by webmonkey47 on 2008-11-26
> **Peter09 said:**
> PHP by default does not provide command line support. It is setup to be run from apache.

You need to download the cli.

```
sudo apt-get install php5-cli
```
ok tried both those suggestions and this was the output:

chris@chris-laptop:~$ sudo apt-get install php5 libapache2-mod-php5
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5 is already the newest version.
libapache2-mod-php5 is already the newest version.
libapache2-mod-php5 set to manually installed.
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libclucene0ldbl libfreebob0 libwildmidi0
  libqt4-opengl graphicsmagick libdc1394-22 pinentry-gtk2
  kdebase-runtime-data-common libsoundtouch1c2 libjack0 phonon libopenspc0
  libfftw3-3 kde-icons-oxygen librasqal0 libakonadiprivate1 kdelibs5-data
  gnupg-agent freepats libqt4-svg phonon-backend-gstreamer libstreamanalyzer0
  libphonon4 libcdaudio1 libkonq5-templates libstreams0 libraptor1
  libgraphicsmagick1 kdebase-runtime-data raptor-utils kdepimlibs-data libofa0
  libmms0 libiptcdata0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@chris-laptop:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                 ... waiting                                                             [ OK ]
chris@chris-laptop:~$ sudo apt-get install php5-cli
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5-cli is already the newest version.
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0 libclucene0ldbl libfreebob0 libwildmidi0
  libqt4-opengl graphicsmagick libdc1394-22 pinentry-gtk2
  kdebase-runtime-data-common libsoundtouch1c2 libjack0 phonon libopenspc0
  libfftw3-3 kde-icons-oxygen librasqal0 libakonadiprivate1 kdelibs5-data
  gnupg-agent freepats libqt4-svg phonon-backend-gstreamer libstreamanalyzer0
  libphonon4 libcdaudio1 libkonq5-templates libstreams0 libraptor1
  libgraphicsmagick1 kdebase-runtime-data raptor-utils kdepimlibs-data libofa0
  libmms0 libiptcdata0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

This does not mean a lot to me other than I need to uninstall a lot of stuff.

---

### Post by webmonkey47 on 2008-11-26
> **mbeach said:**
> from: [http://ubuntuforums.org/showthread.php?t=979567](http://ubuntuforums.org/showthread.php?t=979567)

could also try:
sudo apt-get install php5 libapache2-mod-php5
Sorry mbeach just noticed the web link on your post. will follow through those posts.

and thanks to both of you for very prompt response.. much quicker than those openSuse guys :-)

---

### Post by fatphilthethird on 2008-11-26
Ensure your apache httpd.conf file allows php files 

[http://lamphowto.com/](http://lamphowto.com/)

> To ensure your PHP files are properly interpreted, and not just downloaded as text files, remove the # at the beginning of the lines which read:
#AddType application/x-httpd-php .php
#AddType application/x-httpd-php-source .phps 

---

### Post by webmonkey47 on 2008-11-26
> **fatphilthethird said:**
> Ensure your apache httpd.conf file allows php files 

[http://lamphowto.com/](http://lamphowto.com/)
I've just gone to httpd.conf in /etc/apache2 and it is completely blank.. is there anywhere else I should be looking for this file?  asking this because my previous experience with linux was opensuse and a few things seem to be different with Ubuntu so just checking.

---

### Post by fatphilthethird on 2008-11-26
Looking at this:

[http://ubuntuforums.org/showthread.php?t=278531](http://ubuntuforums.org/showthread.php?t=278531)

it seems that apache2.conf is the new httpd.conf

see if php files have been allowed in there

---

### Post by webmonkey47 on 2008-11-26
> **fatphilthethird said:**
> Looking at this:

[http://ubuntuforums.org/showthread.php?t=278531](http://ubuntuforums.org/showthread.php?t=278531)

it seems that apache2.conf is the new httpd.conf

see if php files have been allowed in there
Thanks for that, just checked apache2.conf and there is no reference to php in it. Will add those two lines and see what happens.

---

### Post by webmonkey47 on 2008-11-26
Just updated apache2.conf with the lines: 

AddType application/x-httpd-php .php
AddType application/x-httpd-php-source .phps 

and restarted apache but problem still exists..

---

### Post by bodhi.zazen on 2008-11-26
See this post :

[http://ubuntuforums.org/showpost.php?p=5780073&postcount=12](http://ubuntuforums.org/showpost.php?p=5780073&postcount=12)

---

### Post by dandellion on 2008-11-28
I had the same problem....

First, be sure to type localhost:// and not file:// (yes, it's simple and obvious, and quite possible)

Second, if after attempt to restart apache you get error message that apache *could not reliably determine the server's fully qualified domain name, using 0.0.9.116 for ServerName* then open /etc/apache2/httpd.conf and type```
 ServerName localhost
```
```
restart apache now sudo apache2ctl restart
```

thanks to [http://www.linuxquestions.org/questions/linux-server-73/apache-giving-the-error-could-not-determine-the-servers-fully-qualified-domain-name-280677/#post1438486]("http://www.linuxquestions.org/questions/linux-server-73/apache-giving-the-error-could-not-determine-the-servers-fully-qualified-domain-name-280677/#post1438486")

---

### Post by mbeach on 2008-12-09
for the record on this thread in case others are after this same info, there will be no reference to php in the apache2.conf file.  Apache is more modular now in that the php specific stuff will be in:
/etc/apache2/mods-available/php5.conf
/etc/apache2/mods-available/php5.load

For the DirectoryIndex see
/etc/apache2/mods-available/dir.conf
you might need to add a index.php there

To enable a mod (which should have been done automatically)
sudo a2enmod php5
which will create a link in .../mods-enabled pointing to .../mods-available
see the following for more info:
[http://www.debian-administration.org/articles/207](http://www.debian-administration.org/articles/207)

You'll see in apache2.conf, that all the mods in /etc/apache2/mods-enabled are included.  Look for the 
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
lines.  This is the reason you are not finding references to php in your apache2.conf file.

---

### Post by rrll1977 on 2009-05-18
Hi all,

Has anybody ever worked with mod_rewrite and mod_userdir on LAMPP?

It appears that mod_rewrite doesn't work with the user's websites (located on /home/user/public_html), although it appears to work fine with the home server websites (on /opt/lampp/htdocs)

Regards

---

