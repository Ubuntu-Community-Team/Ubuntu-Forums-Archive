---
title: "install Zend Optimizer in 8.10"
date: 2008-11-10
forum: General Help
---

### Post by realthor on 2008-11-10
Hi all, I am trying for some time to install Zend Optimizer in ubuntu as I have some scripts that were compressed (or whatever) by this tool and my php seem not to take into account this installation.

I downloaded Zend Optimizer from Zend website and installed it by ./install.sh...it asked at some point my php.ini location, I put /etc then asked if I used apache, said NO...and the installation finished.

On [this site]("http://www.ehow.com/how_2090985_optimizer-redhat-enterprise-linux-rhel.html") it sais that when I run php -v i should get "something similar to PHP 5.2.3 (cli) (built: Jun 7 2007 08:59:02) Copyright (c) 1997-2007 The PHP Group Zend Engine v2.2.0, Copyright (c) 1998-2007 Zend Technologies with Zend Extension Manager v1.2.0, Copyright (c) 2003-2007, by Zend Technologies with Zend Optimizer v3.3.0, Copyright (c) 1998-2007, by Zend Technologies "

but in my case:

 php -v
PHP 5.2.6-2ubuntu4 with Suhosin-Patch 0.9.6.2 (cli) (built: Oct 14 2008 20:06:32) 
Copyright (c) 1997-2008 The PHP Group
Zend Engine v2.2.0, Copyright (c) 1998-2008 Zend Technologies

All my php.ini files on the system have all those lines the site specifies:

:/etc$ more php.ini


[Zend]
zend_extension_manager.optimizer=/usr/local/Zend/lib/Optimizer-3.3.3
zend_extension_manager.optimizer_ts=/usr/local/Zend/lib/Optimizer_TS-3.3.3
zend_optimizer.version=3.3.3
zend_extension=/usr/local/Zend/lib/ZendExtensionManager.so
zend_extension_ts=/usr/local/Zend/lib/ZendExtensionManager_TS.so

The scripts when run complain about not finding ZendOptimizer:

Warning: unknown mime-type for "<p>In order to run it, please install the freely available <a href="http://www.zend.com/store/products/zend-optimizer.php">Zend Optimizer</a>, version 2.1.0 or later.</p>\n"

I have installed 3.3.3 as you can see above.

Any help would be appreciated. Thanks.

---

### Post by quzomatic on 2008-12-17
I had the same issue.  I found out that I installed the wrong version.  I installed 32bit version yet it should have been the 64bit version.  Everything works fine now.

Also check if your PHP5 enable_versioning is disabled

---

### Post by chris71p on 2008-12-27
Hi All
I am new in Linux,and I try to install Zend Optimizer I follow instruction no documents but I have Error massage  "You need root privileges to run this script!" Ubuntu doz not let me log in as Root:confused:
may be I`m doing something wrong. Any Help how to install Zend optimizer?:confused:    
I am completely lost :confused::confused::confused:

Thanks
Chris.

---

### Post by theozzlives on 2008-12-27
do "sudo" (without the quotes) command you're trying to execute

---

