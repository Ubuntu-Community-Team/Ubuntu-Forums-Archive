---
title: "installing Xinc"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by mitjab on 2009-10-27
sudo pear install --alldeps pear.xinc.eu/Xinc-2.0.0b196
Unknown remote channel: pear.phing.info
Unknown remote channel: components.ez.no
Unknown remote channel: components.ez.no

Fatal error: Allowed memory size of 8388608 bytes exhausted (tried to allocate 16 bytes) in /usr/share/php/PEAR/Registry.php on line 1145

Call Stack:
    0.0551     234556   1. {main}() /usr/share/php/pearcmd.php:0
    5.0284    2926120   2. PEAR_Command_Common->run() /usr/share/php/pearcmd.php:305
    5.0287    2926120   3. PEAR_Command_Install->doInstall() /usr/share/php/PEAR/Command/Common.php:271
    6.1708    5194012   4. PEAR_Downloader->download() /usr/share/php/PEAR/Command/Install.php:661
    7.3512    6774900   5. PEAR_Downloader_Package->detectDependencies() /usr/share/php/PEAR/Downloader.php:391
    7.3546    6774900   6. PEAR_Downloader_Package->_detect2() /usr/share/php/PEAR/Downloader/Package.php:381
    8.7450    7264264   7. PEAR_Downloader_Package->_detect2Dep() /usr/share/php/PEAR/Downloader/Package.php:502
    8.7540    7264264   8. PEAR_Downloader->_getDepPackageDownloadUrl() /usr/share/php/PEAR/Downloader/Package.php:639
    8.8056    7265688   9. PEAR_Registry->packageInfo() /usr/share/php/PEAR/Downloader.php:972
    8.8121    7265904  10. PEAR_Registry->_packageInfo() /usr/share/php/PEAR/Registry.php:1648
    8.8634    8112412  11. unserialize() /usr/share/php/PEAR/Registry.php:1145

How can i change allowed memory?

I have 40m memory in php.ini

memory_limit = 40M      ; Maximum amount of memory a script may consume (8MB)

---

### Post by BigG123 on 2009-10-27
Change php.ini?  Not to sure.

---

### Post by mitjab on 2009-10-27
SOLVED:

Help with this link
[http://pear.php.net/bugs/bug.php?id=1596](http://pear.php.net/bugs/bug.php?id=1596)


> According to [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg205637.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg205637.html) the solution is to increase the allowed memory size for PEAR. I did this by altering the following line in /usr/bin/pear : exec $PHP -C -q $INCARG -d output_buffering=1 $INCDIR/pearcmd.php "$@" to exec $PHP -C -q $INCARG -d output_buffering=1 -d memory_limit=36M $INCDIR/pearcmd.php "$@" cheers, gustavo

---

