---
title: "to install the PECL uploadprogress library"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by lisssina on 2009-05-19
In the page of report of my drupal site, the upload progress module gives me an error. The error is the following:

"Upload progress    Not trained 
Your server is capable of displaying file upload progress, but does not have the required libraries. It is recommended to install the PECL uploadprogress library (prefered) or to install APC." 

I have tried to install the PECL uploadprogress library, but I have not succeeded there. There is someone who is able to point out whether to find the instructions for a correct installation of such bookstores. On my server Ubuntu 8.10 turns.

---

### Post by zargh on 2009-06-25
Install the PHP developer package for the version of PHP you're using. For example, in case of php5 run:
$ sudo apt-get install php5-dev
 
Install the PECL uploadprogress library:
$ sudo pecl install uploadprogress

Open php.ini :
$ sudo gedit /etc/php5/apache2/php.ini
Add the line "extension=uploadprogress.so" to php.ini

Restart apache:
$ sudo /etc/init.d/apache2 restart

---

### Post by clarkburbidge on 2009-08-02
I also needed php-pear, so my command was:

```

sudo apt-get install php5-dev php-pear

```

Otherwise the

```

sudo pecl install uploadprogress

```

didn't work for me...

---

### Post by fduppa on 2009-12-28
> **zargh said:**
> Install the PHP developer package for the version of PHP you're using. For example, in case of php5 run:
$ sudo apt-get install php5-dev
 
Install the PECL uploadprogress library:
$ sudo pecl install uploadprogress

Open php.ini :
$ sudo gedit /etc/php5/apache2/php.ini
Add the line "extension=uploadprogress.so" to php.ini

Restart apache:
$ sudo /etc/init.d/apache2 restart

this was really useful. Sorry for the bump.. i wanted really badly to say

THANKS

---

### Post by spikyjt on 2010-02-28
Just to add: the Debian (and therefore Ubuntu) way to add the module to php is to add a file like /etc/php5/apache2/conf.d/uploadprogress.ini containing extension=uploadprogress.so which will be picked up by php.ini. This means that php can be upgraded without having to re-edit the default php.ini file.

---

### Post by 1jackjack on 2010-04-29
Thanks zargh and clarkburbidge, those instructions worked a charm. Just to add that when I installed uploadprogress, at the end I got this:
"configuration option "php_ini" is not set to php.ini location"
But everything still worked anyway... is this anything to be worried about?

Cheers

---

### Post by Francewhoa on 2010-05-08
Thanks all :)

**I wrote a how-to handbook for Ubuntu at [http://drupal.org/node/793262](http://drupal.org/node/793262)**

---

### Post by 1jackjack on 2010-07-28
Note: Upgrade to Lucid broke this. The fix was to re-install uploadprogress with pecl i.e.

sudo pecl uninstall uploadprogress
sudo pecl install uploadprogress

Then re-add the line in php.ini if it was removed, and restart apache.

---

### Post by jannol on 2010-08-10
> **spikyjt said:**
> Just to add: the Debian (and therefore Ubuntu) way to add the module to php is to add a file like /etc/php5/apache2/conf.d/uploadprogress.ini containing extension=uploadprogress.so which will be picked up by php.ini. This means that php can be upgraded without having to re-edit the default php.ini file.

Right you are and also just to mention it, the "right" way to add it also works for suphp and possibly for other variants without any further adding in other files.

---

### Post by edsonmatos on 2011-02-02
In my case, I had to put uploadprogress.so in

/opt/lampp/lib/php/extensions/no-debug-non-zts-20090626/

and edited php.ini in

/opt/lampp/etc/

Then

/opt/lampp/lampp restart

That's all.):P

---

### Post by CJScully on 2011-03-17
I get the following when running pecl install uploadprogress

downloading uploadprogress-1.0.1.tgz ...
Starting to download uploadprogress-1.0.1.tgz (8,536 bytes)
.....done: 8,536 bytes
4 source files, building
running: phpize
Configuring for:
PHP Api Version:         20090626
Zend Module Api No:      20090626
Zend Extension Api No:   220090626
/usr/bin/phpize: 209: /tmp/pear/temp/uploadprogress/build/shtool: Permission denied
Cannot find autoconf. Please check your autoconf installation and the
$PHP_AUTOCONF environment variable. Then, rerun this script.

ERROR: `phpize' failed

The autoconf package is installed on the server. I'm stuck. Can't figure out what could be causing this.

---

### Post by HonoredMule on 2011-11-22
CJScully, you need to have php5-dev installed, not just autoconf.

---

### Post by snovak on 2012-01-01
I wound up with a build error.  Turns out you need build essentials too (in 11.10)

```

sudo apt-get install build-essential

```

---

### Post by progone on 2012-02-10
> **zargh said:**
> Install the PHP developer package for the version of PHP you're using. For example, in case of php5 run:
$ sudo apt-get install php5-dev
 
Install the PECL uploadprogress library:
$ sudo pecl install uploadprogress

Open php.ini :
$ sudo gedit /etc/php5/apache2/php.ini
Add the line "extension=uploadprogress.so" to php.ini

Restart apache:
$ sudo /etc/init.d/apache2 restart

The above partially work with 11.10. After you complete the steps above. You can put the apc.rfc# in the apc.ini file instead of the php.ini

try this: ```
locate apc.ini

```
Results for me:  /etc/php5/conf.d/apc.ini
```
gedit /etc/php5/conf.d/apc.ini
```
apc.ini opens, and add if its not there
```
extension=apc.so
apc.enabled=1
apc.shm_size=30
apc.rfc1867 = 1
```
Please NOTE: **rfc1867** may be different upon your configuration.  Please which ever rfc#### Drupal gives to you for line 4.  You will get this RFC# from the status page.  

Upon a successful completion your message will look like this on the status page:  [PHP]Upload progress	Enabled (APC RFC1867)
Your server is capable of displaying file upload progress using APC RFC1867. 
Note that only one upload at a time is supported. It is recommended to use
 the PECL uploadprogress library if possible.[/PHP]

---

### Post by ellenbo on 2012-05-22
Thank you all for the help. I also ended up having to use:

```
$ sudo apt-get install php5-dev php-pear
```

I added the line "extension=uploadprogress.so" to the very top of php.ini. Is this the right place to put it? It's working for now...

---

### Post by selwynpolit on 2013-01-28
> **clarkburbidge said:**
> 

```

sudo pecl install uploadprogress

```

...

after trying the command above, I got:
config.status: executing libtool commands
running: make
sh: 1: make: not found
ERROR: `make' failed
so I had to run:
```

sudo apt-get install make

```

then I could run the 
```

sudo pecl install uploadprogress

```
 now for updating the ini correctly

---

