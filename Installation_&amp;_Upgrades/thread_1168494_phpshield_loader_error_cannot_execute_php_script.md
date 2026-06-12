---
title: "phpshield loader error cannot execute php script"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by nyash on 2009-05-24
Hello

I had installed a popular video-sharing script (PHPMOTION) on my ubuntu  server edition 9.04

Everything works except converting videos.

I made a cron job, command:

> php -q /var/www/convertor.php (This command is supposed to convert videos to a flash format)

and this is the error I am getting:

> From: [EMAIL="root@admin.pptv.pl"]root@admin.pptv.pl[/EMAIL] (Cron Daemon)
To: [EMAIL="zb1g@admin.pptv.pl"]zb1g@admin.pptv.pl[/EMAIL]
Subject: Cron <zb1g@pptv> php -q /var/www/convertor.php
Content-Type: text/plain; charset=UTF-8
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/home/zb1g>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=zb1g>
Message-Id: <[EMAIL="20090523074501.4094B74E53E@pptv.pptv.pl"]20090523074501.4094B74E53E@pptv.pptv.pl[/EMAIL]>
Date: Sat, 23 May 2009 09:45:01 +0200 (CEST)


Warning: dl(): Dynamically loaded extensions aren't enabled in /var/www/classes/config.php on line 2
PHP script <B>/var/www/classes/config.php</B> is protected by <A HREF="[http://www.phpshield.com/](http://www.phpshield.com/)">phpSHIELD</A> and requires the phpSHIELD loader <B>php$shield.5.2.lin</B>. The phpSHIELD loader has not been installed, or is not installed correctly. Please visit the <A HREF="[http://www.phpshield.com/loader](http://www.phpshield.com/loader)$phpSHIELD php encoder</A> site to download required loader.


I have added the appropriate loader file (phpshield.5.2.lin) to this folder:
> /usr/lib/php5/20060613+lfs/phpshield

I have edited: 
> /etc/php5/apache2/php.ini 

and added in the Dynamic Extensions section:
> extension = phpshield/phpshield.5.2.lin

I also have the loader file (phpshield.5.2.lin) in this folder:
> /var/www/phpshield


It seems that the loader partially works, because  without adding it I wasn't able to access the setup section of the video-sharing script (It gave the same error like now)

But there's a catch to it somewhere and it just won't execute the convertor.php file and I am really out of ideas.

I would appreciate any help. 
Thanks in advance!

PHPInfo file:
[http://pptv.pl/phpinfo.php](http://pptv.pl/phpinfo.php)

---

