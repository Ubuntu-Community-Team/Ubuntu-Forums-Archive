---
title: "Installing APC for PHP (HELP!)"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by icebofh on 2009-03-31
Experiencing weirdness on Ubuntu 8.04. 

I had previously installed APC 3.0.19 just fine using "sudo pecl install apc". I was going to try out the beta version tonight so I uninstalled apc and tried "sudo pecl install apc-beta". It failed miserably complaining the libtool did not exist. What's strange is that I was previously able to install apc just fine.


Now when I try to reinstall the stable version, I get the same error messages. 

```

 sudo pecl install apc
downloading APC-3.0.19.tgz ...
Starting to download APC-3.0.19.tgz (115,735 bytes)
.........................done: 115,735 bytes
47 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20060613
Zend Extension Api No:   220060519
cp: cannot stat `ltmain.sh': No such file or directory
cat: /usr/share/aclocal/ltsugar.m4: No such file or directory
cat: /usr/share/aclocal/ltversion.m4: No such file or directory
cat: /usr/share/aclocal/lt~obsolete.m4: No such file or directory
cat: /usr/share/aclocal/ltoptions.m4: No such file or directory
 1. Use apxs to set compile flags (if using APC with Apache)? : yes

1-1, 'all', 'abort', or Enter to continue: 

....

config.status: creating config.h
running: make
/bin/bash /var/tmp/pear-build-root/APC-3.0.19/libtool --mode=compile gcc -DLINUX=2 -D_GNU_SOURCE -D_LARGEFILE64_SOURCE -D_REENTRANT -I/usr/include/apr-1.0 -I/usr/include/openssl -I/usr/include/postgresql -I/usr/include/xmltok -pthread -I. -I/tmp/pear/temp/APC -DPHP_ATOM_INC -I/var/tmp/pear-build-root/APC-3.0.19/include -I/var/tmp/pear-build-root/APC-3.0.19/main -I/tmp/pear/temp/APC -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64  -I/usr/include/php5 -DHAVE_CONFIG_H  -g -O2   -c /tmp/pear/temp/APC/apc.c -o apc.lo
/bin/bash: /var/tmp/pear-build-root/APC-3.0.19/libtool: No such file or directory
make: *** [apc.lo] Error 127
ERROR: `make' failed


```

Looking at a similar thread, the suggestion was to make sure php5-dev and apache2-dev were installed and it's already installed on my system previously. So seriously scratching my head as to why the build will suddenly fail. Need help as my site is down right now.. Thanks!

---

### Post by icebofh on 2009-03-31
Well, 

It turns out that /usr/lib/php5/build/ltmain.sh is linked to the wrong place. It needs to point to ../../../share/libtool/ltmain.sh instead of ../../../share/libtool/config/ltmain.sh

After fixing this, things worked fine.

---

