---
title: "Broken package (libapache-mod-perl) on upgrade to Ubuntu 8.10"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by e-a-c on 2009-01-19
I was trying to upgrade from Ubuntu 8.04 LTS to Ubuntu 8.10, and the upgrade failed with an error on the "libapache-mod-perl" package. Now that package is broken and I cannot remove it, or install/remove/upgrade anything else, for that matter. 
Here are my attempts at resolving the problem so far:
```

**ecassell@ecassell:~$ sudo apt-get remove libapache-mod-perl**
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 libwvstreams4.3-extras menu libmtp6 libopenal0a libneon26 libavutil1d python-pexpect libdc1394-13 libsnmp10 linux-restricted-modules-2.6.17-12-generic libicu36 python-twisted-web
  libwxgtk2.6-0 g++-4.1 python-pycurl libglew1.4 libdns32 libcamel1.2-10 libpostproc1d emacs22-bin-common emacs22-common libgpod2 libisccc30 libavformat1d linux-restricted-modules-2.6.17-10-generic
  libstdc++6-4.1-dev libsvg1 libxosd2 libpcrecpp0 libalut0 emacsen-common libhunspell-1.1-0 ecj liblwres30 gutsy-wallpapers libkonq4 libwxbase2.6-0 libhtml-simpleparse-perl libpoppler2 libgtkhtml2.0-cil
  libdirectfb-0.9-25 libbind9-30 openoffice.org-hyphenation libdbus-qt-1-1c2 networkstatus libwvstreams4.3-base libiso9660-4 libmime-perl libisccfg30 libavcodec1d libgucharmap6 libdb4.2 libdb4.5
  libtotem-plparser7 python-smartpm linux-restricted-modules-2.6.22-14-generic libisc32 linux-restricted-modules-2.6.20-16-generic libnss3-0d feisty-gdm-themes libltdl3 libntfs-3g12 libpoppler-glib2
  o3read librsvg2.0-cil
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libapache-mod-perl
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1303kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 268474 files and directories currently installed.)
Removing libapache-mod-perl ...
Error: libphp5.so does not have a corresponding .info file.
The above errors might cause apache to not work properly or start
Please refer to the documentation on how to fix it or report it to
Debian Apache Mailing List <debian-apache@lists.debian.org> if in doubt
on how to proceed
dpkg: error processing libapache-mod-perl (--remove):
 subprocess pre-removal script returned error exit status 20
Error: libphp5.so does not have a corresponding .info file.
The above errors might cause apache to not work properly or start
Please refer to the documentation on how to fix it or report it to
Debian Apache Mailing List <debian-apache@lists.debian.org> if in doubt
on how to proceed
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 128
Errors were encountered while processing:
 libapache-mod-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)

**ecassell@ecassell:~$ sudo dpkg --configure libapache-mod-perl**
dpkg: dependency problems prevent configuration of libapache-mod-perl:
 libapache-mod-perl depends on libperl5.8 (>= 5.8.8); however:
  Package libperl5.8 is not installed.
dpkg: error processing libapache-mod-perl (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libapache-mod-perl

**ecassell@ecassell:~$ sudo apt-get install libperl5.8**
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Package libperl5.8 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  perl-base
E: Package libperl5.8 has no installation candidate

**ecassell@ecassell:~$ sudo apt-get install perl-base**
Reading package lists... Done
Building dependency tree      
Reading state information... Done
perl-base is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libapache-mod-perl: Depends: libperl5.8 (>= 5.8.8) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by e-a-c on 2009-01-19
Fixed! I found this post and decided to give it a try:
[http://lists.debian.org/debian-apache/2007/06/msg00089.html](http://lists.debian.org/debian-apache/2007/06/msg00089.html)

I manually created a file called "501mod_php5.info" in /usr/lib/apache/1.3
```
LoadModule: php5_module /usr/lib/apache/1.3/libphp5.so
```

After that I was finally able to remove the libapache-mod-perl package

---

