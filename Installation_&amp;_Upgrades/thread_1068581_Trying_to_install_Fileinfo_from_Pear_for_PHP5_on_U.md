---
title: "Trying to install Fileinfo from Pear for PHP5 on Ubuntu Server 8.10"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by Ford AntiTrust on 2009-02-13
I trying to install Fileinfo from Pear for PHP5 on Ubuntu Server 8.10

This is what happens... any ideas?

My Server configuration
Linux ns1.com 2.6.27-11-server #1 SMP Thu Jan 29 20:13:12 UTC 2009 x86_64

PHP Version 5.2.8-0.dotdeb.1
----------------------------------------------
This server is protected with the Suhosin Patch 0.9.6.3
Copyright (c) 2006 Hardened-PHP Project
----------------------------------------------
This program makes use of the Zend Scripting Language Engine:
Zend Engine v2.2.0, Copyright (c) 1998-2008 Zend Technologies
    with Suhosin v0.9.27, Copyright (c) 2007, by SektionEins GmbH
----------------------------------------------
This program was built by Dotdeb.
----------------------------------------------

--------- Command --------- 
$sudo pecl install fileinfo

--------- Output  --------- 
WARNING: "pear/Fileinfo" is deprecated in favor of "channel://php-src/ext/fileinfo/in php sources"
downloading Fileinfo-1.0.4.tgz ...
Starting to download Fileinfo-1.0.4.tgz (5,835 bytes)
.....done: 5,835 bytes
3 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
cp: cannot stat `libtool.m4': No such file or directory
cp: cannot stat `ltmain.sh': No such file or directory
cat: ./build/libtool.m4: No such file or directory
configure.in:8: warning: LT_AC_PROG_SED is m4_require'd but not m4_defun'd
aclocal.m4:2628: PHP_CONFIG_NICE is expanded from...
configure.in:8: the top level
configure.in:137: error: possibly undefined macro: AC_PROG_LIBTOOL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure:1845: error: possibly undefined macro: LT_AC_PROG_SED
ERROR: `phpize' failed

---

### Post by lemming465 on 2009-02-14
Um, did you run *apt-get install build-essential* before doing this?

---

### Post by Ford AntiTrust on 2009-02-15
> **lemming465 said:**
> Um, did you run *apt-get install build-essential* before doing this?

Yes, I *apt-get install build-essential* already.

---

### Post by scrr on 2010-02-11
Just had the same problem.

Solution: First do:

apt-get install php-pear php5-dev libmagic-dev

Then do:

pecl install fileinfo

---

