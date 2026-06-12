---
title: "[SOLVED] same error whenever I use apt-get"
date: 2008-09-06
forum: General Help
---

### Post by MaxIBoy on 2008-09-06
Something broke. Here's an example:

```
maxtothemax@maxtothemax-desktop:~$ sudo apt-get install abiword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  abiword: Depends: abiword-common (>= 2.4.1) but it is not going to be installed
  libgtkglext1-ruby1.8: Depends: libgtkglext1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


maxtothemax@maxtothemax-desktop:~$ #the following happens whenever I run "sudo apt-get -f install"
maxtothemax@maxtothemax-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  x11proto-xinerama-dev x11proto-render-dev libxi-dev libxmu-headers libxrender-dev libqt4-core libpng12-dev libsqlite0-dev libfontconfig1-dev
  libxcursor-dev x11proto-randr-dev libxmu-dev libqt4-sql libfreetype6-dev x11proto-fixes-dev liblcms1-dev libpq-dev libxrandr-dev libexpat1-dev
  libxft-dev libxfixes-dev libmng-dev libxinerama-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgtkglext1
The following NEW packages will be installed:
  libgtkglext1
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
3 not fully installed or removed.
Need to get 0B/126kB of archives.
After this operation, 414kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 139252 files and directories currently installed.)
Unpacking libgtkglext1 (from .../libgtkglext1_1.2.0-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgdkglext-x11-1.0.so.0.0.0', which is also in package libgtkglext-1.0-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
maxtothemax@maxtothemax-desktop:~$ 

```


More examples:

```
maxtothemax@maxtothemax-desktop:~$ sudo apt-get install inkscape
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  inkscape: Depends: libmagick++10 but it is not going to be installed
  libgtkglext1-ruby1.8: Depends: libgtkglext1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
maxtothemax@maxtothemax-desktop:~$ 

```


```
maxtothemax@maxtothemax-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libgtkglext1-ruby1.8: Depends: libgtkglext1 but it is not installed
E: Unmet dependencies. Try using -f.
maxtothemax@maxtothemax-desktop:~$ 

```

---

### Post by pytheas22 on 2008-09-06
What happens if you run:
```

sudo apt-get autoremove
sudo apt-get -f install
```

---

### Post by MaxIBoy on 2008-09-06
Already tried that:


```
maxtothemax@maxtothemax-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libgtkglext1-ruby1.8: Depends: libgtkglext1 but it is not installed
E: Unmet dependencies. Try using -f.


maxtothemax@maxtothemax-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  x11proto-xinerama-dev x11proto-render-dev libxi-dev libxmu-headers
  libxrender-dev libqt4-core libpng12-dev libsqlite0-dev libfontconfig1-dev
  libxcursor-dev x11proto-randr-dev libxmu-dev libqt4-sql libfreetype6-dev
  x11proto-fixes-dev liblcms1-dev libpq-dev libxrandr-dev libexpat1-dev
  libxft-dev libxfixes-dev libmng-dev libxinerama-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgtkglext1
The following NEW packages will be installed:
  libgtkglext1
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
3 not fully installed or removed.
Need to get 0B/126kB of archives.
After this operation, 414kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 139252 files and directories currently installed.)
Unpacking libgtkglext1 (from .../libgtkglext1_1.2.0-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgdkglext-x11-1.0.so.0.0.0', which is also in package libgtkglext-1.0-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
maxtothemax@maxtothemax-desktop:~$ 

```

---

### Post by MaxIBoy on 2008-09-06
maxtothemax@maxtothemax-desktop:~$ sudo apt-get install libgtkglext1
[sudo] password for maxtothemax: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  x11proto-xinerama-dev x11proto-render-dev libxi-dev libxmu-headers
  libxrender-dev libqt4-core libpng12-dev libsqlite0-dev libfontconfig1-dev
  libxcursor-dev x11proto-randr-dev libxmu-dev libqt4-sql libfreetype6-dev
  x11proto-fixes-dev liblcms1-dev libpq-dev libxrandr-dev libexpat1-dev
  libxft-dev libxfixes-dev libmng-dev libxinerama-dev
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libgtkglext1
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
3 not fully installed or removed.
Need to get 0B/126kB of archives.
After this operation, 414kB of additional disk space will be used.
(Reading database ... 139252 files and directories currently installed.)
Unpacking libgtkglext1 (from .../libgtkglext1_1.2.0-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgdkglext-x11-1.0.so.0.0.0', which is also in package libgtkglext-1.0-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
maxtothemax@maxtothemax-desktop:~$

---

### Post by kinemagician on 2008-09-06
Similar problem I get the following error message

E: Sub-process /usr/bin/dpkg returned an error code (1)

running a sudo apt-get install enscript

---

### Post by pytheas22 on 2008-09-06
MaxIBoy,

What happens if you try:
```

sudo apt-get install -f abiword
sudo apt-get install -f libgtkglext1
```

kinemagician,

Could you please post the full output that you get when you try to run "sudo apt-get install enscript?"

---

### Post by MaxIBoy on 2008-09-06
```
maxtothemax@maxtothemax-desktop:~$ sudo apt-get install -f abiword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  abiword: Depends: abiword-common (>= 2.4.1) but it is not going to be installed
  libgtkglext1-ruby1.8: Depends: libgtkglext1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


maxtothemax@maxtothemax-desktop:~$ sudo apt-get install -f libgtkglext1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  x11proto-xinerama-dev x11proto-render-dev libxi-dev libxmu-headers libxrender-dev libqt4-core libpng12-dev libsqlite0-dev libfontconfig1-dev
  libxcursor-dev x11proto-randr-dev libxmu-dev libqt4-sql libfreetype6-dev x11proto-fixes-dev liblcms1-dev libpq-dev libxrandr-dev libexpat1-dev
  libxft-dev libxfixes-dev libmng-dev libxinerama-dev
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libgtkglext1
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
3 not fully installed or removed.
Need to get 0B/126kB of archives.
After this operation, 414kB of additional disk space will be used.
(Reading database ... 139252 files and directories currently installed.)
Unpacking libgtkglext1 (from .../libgtkglext1_1.2.0-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgdkglext-x11-1.0.so.0.0.0', which is also in package libgtkglext-1.0-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
maxtothemax@maxtothemax-desktop:~$ 
```



Perhaps apt itself is broken?



EDIT: Some background story: a couple of days ago I needed to get a ruby script working, so I installed a whole ton of dependencies. I don't remember exactly but I think some of the repository versions were out of date and didn't work, so I downloaded and manually installed them (but I'm not sure about that, I remember doing this pretty late and I was tired and had a cold.) Since then the automatic update hasn't been able to install every single update and I'm getting these errors. The ruby script still works though, so I don't think anything got overwritten with the repository versions. I'm not sure which ones are messed up, but I think that's the origin of the problem.

---

### Post by pytheas22 on 2008-09-06
Yes, probably either apt is broken, or there's a serious issue with your sources list.  What is the output of:
```

cat /etc/apt/sources.list
```

---

### Post by MaxIBoy on 2008-09-07
maxtothemax@maxtothemax-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
maxtothemax@maxtothemax-desktop:~$

---

### Post by MaxIBoy on 2008-09-07
This is seriously hampering the usability of my system.

---

### Post by oldos2er on 2008-09-07
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

 Uncomment those last two lines (remove the # mark), then in a terminal run "sudo aptitude update && sudo aptitude upgrade". Leave the rest of sources.list as is.

---

### Post by pytheas22 on 2008-09-07
Yes, please try editing /etc/apt/sources.list as mentioned above; hopefully that will fix things and allow you to run "sudo apt-get install -f" successfully.  Please let us know.

---

### Post by MaxIBoy on 2008-09-07
Still not happening.

```
maxtothemax@maxtothemax-desktop:~$ sudo aptitude update && sudo aptitude upgrade
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Get:1 http://archive.canonical.com hardy Release.gpg [189B]
Ign http://archive.canonical.com hardy/partner Translation-en_US
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Get:2 http://archive.canonical.com hardy Release [6998B]
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-security Release.gpg
Ign http://us.archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release      
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://us.archive.ubuntu.com hardy-security Release                  
Hit http://us.archive.ubuntu.com hardy/main Packages                
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Get:3 http://archive.canonical.com hardy/partner Packages [3016B]
Hit http://us.archive.ubuntu.com hardy-security/main Packages
Hit http://us.archive.ubuntu.com hardy-security/restricted Packages
Hit http://us.archive.ubuntu.com hardy-security/main Sources
Hit http://us.archive.ubuntu.com hardy-security/restricted Sources
Hit http://us.archive.ubuntu.com hardy-security/universe Packages
Hit http://us.archive.ubuntu.com hardy-security/universe Sources
Hit http://us.archive.ubuntu.com hardy-security/multiverse Packages 
Hit http://us.archive.ubuntu.com hardy-security/multiverse Sources
Get:4 http://archive.canonical.com hardy/partner Sources [1376B]
Fetched 11.6kB in 2s (5428B/s)
Reading package lists... Done
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have unmet dependencies:
  libgtkglext1-ruby1.8: Depends: libgtkglext1 but it is not installable
maxtothemax@maxtothemax-desktop:~$ 

```


```
maxtothemax@maxtothemax-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  x11proto-xinerama-dev x11proto-render-dev libxi-dev libxmu-headers
  libxrender-dev libqt4-core libpng12-dev libsqlite0-dev libfontconfig1-dev
  libxcursor-dev x11proto-randr-dev libxmu-dev libqt4-sql libfreetype6-dev
  x11proto-fixes-dev liblcms1-dev libpq-dev libxrandr-dev libexpat1-dev
  libxft-dev libxfixes-dev libmng-dev libxinerama-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgtkglext1
The following NEW packages will be installed:
  libgtkglext1
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
3 not fully installed or removed.
Need to get 0B/126kB of archives.
After this operation, 414kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 139252 files and directories currently installed.)
Unpacking libgtkglext1 (from .../libgtkglext1_1.2.0-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgdkglext-x11-1.0.so.0.0.0', which is also in package libgtkglext-1.0-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
maxtothemax@maxtothemax-desktop:~$ 

```

---

### Post by pytheas22 on 2008-09-07
What is the output of this:
```

sudo apt-get remove --purge libgtkglext*
sudo apt-get install -f
```

---

### Post by MaxIBoy on 2008-09-07
```
maxtothemax@maxtothemax-desktop:~$ sudo apt-get remove --purge libgtkglext*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtkglext-1.0-0_1.2.0-4_i386.deb


maxtothemax@maxtothemax-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  x11proto-xinerama-dev x11proto-render-dev libxi-dev libxmu-headers
  libxrender-dev libqt4-core libpng12-dev libsqlite0-dev libfontconfig1-dev
  libxcursor-dev x11proto-randr-dev libxmu-dev libqt4-sql libfreetype6-dev
  x11proto-fixes-dev liblcms1-dev libpq-dev libxrandr-dev libexpat1-dev
  libxft-dev libxfixes-dev libmng-dev libxinerama-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgtkglext1
The following NEW packages will be installed:
  libgtkglext1
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
3 not fully installed or removed.
Need to get 0B/126kB of archives.
After this operation, 414kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 139252 files and directories currently installed.)
Unpacking libgtkglext1 (from .../libgtkglext1_1.2.0-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgdkglext-x11-1.0.so.0.0.0', which is also in package libgtkglext-1.0-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
maxtothemax@maxtothemax-desktop:~$ 

```

Think I'll have to abandon ship? (lucky I've got a home partition.)

---

### Post by pytheas22 on 2008-09-07
Yeah, reinstalling might end up being the best option.  But first let's try using aptitude instead of apt-get; maybe it will work better.  Does this do anything:
```

sudo aptitude remove --purge libgtkglext*
```

If aptitude works, you could always use it to reinstall apt-get.  But if the problem lies lower (maybe dpkg), then it will be hard to fix.

---

### Post by MaxIBoy on 2008-09-07
I think that *might* have worked. 
EDIT: On closer inspection of the output, it did not work. Also, apt-get is still broken.
```

maxtothemax@maxtothemax-desktop:~/alienarenainstalls/7.12/source$ sudo aptitude remove --purge libgtkglext*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find package "libgtkglext*".  However, the following
packages contain "libgtkglext*" in their name:
  libgtkglext1-ruby libgtkglext-1.0-0 libgtkglextmm-x11-dev libgtkglext1-ruby1.8 libgtkglextmm-x11-1.2 libgtkglext1-dev libgtkglext1-doc libgtkglext1 
Couldn't find package "libgtkglext*".  However, the following
packages contain "libgtkglext*" in their name:
  libgtkglext1-ruby libgtkglext-1.0-0 libgtkglextmm-x11-dev libgtkglext1-ruby1.8 libgtkglextmm-x11-1.2 libgtkglext1-dev libgtkglext1-doc libgtkglext1 
The following packages are BROKEN:
  libgtkglext1-ruby1.8 
The following packages are unused and will be REMOVED:
  libexpat1-dev{p} libfontconfig1-dev{p} libfreetype6-dev{p} liblcms1-dev{p} libmng-dev{p} libpng12-dev{p} libpq-dev{p} libqt4-core{p} libqt4-sql{p} 
  libsqlite0-dev{p} libxcursor-dev{p} libxfixes-dev{p} libxft-dev{p} libxi-dev{p} libxinerama-dev{p} libxmu-dev{p} libxmu-headers{p} libxrandr-dev{p} 
  libxrender-dev{p} x11proto-fixes-dev{p} x11proto-randr-dev{p} x11proto-render-dev{p} x11proto-xinerama-dev{p} 
The following packages have been automatically kept back:
  winbind 
The following packages have been kept back:
  language-pack-en language-pack-gnome-en libsmbclient samba-common smbclient 
The following partially installed packages will be configured:
  libgtkglext1-ruby ruby-gnome2 
0 packages upgraded, 0 newly installed, 23 to remove and 6 not upgraded.
Need to get 0B of archives. After unpacking 18.8MB will be freed.
The following packages have unmet dependencies:
  libgtkglext1-ruby1.8: Depends: libgtkglext1 but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
libgtkglext1 [1.2.0-0ubuntu1 (hardy)]

Score is 41

Accept this solution? [Y/n/q/?] y
The following packages are unused and will be REMOVED:
  libexpat1-dev{p} libfontconfig1-dev{p} libfreetype6-dev{p} liblcms1-dev{p} libmng-dev{p} libpng12-dev{p} libpq-dev{p} libqt4-core{p} libqt4-sql{p} 
  libsqlite0-dev{p} libxcursor-dev{p} libxfixes-dev{p} libxft-dev{p} libxi-dev{p} libxinerama-dev{p} libxmu-dev{p} libxmu-headers{p} libxrandr-dev{p} 
  libxrender-dev{p} x11proto-fixes-dev{p} x11proto-randr-dev{p} x11proto-render-dev{p} x11proto-xinerama-dev{p} 
The following packages have been automatically kept back:
  winbind 
The following NEW packages will be automatically installed:
  libgtkglext1 
The following packages have been kept back:
  language-pack-en language-pack-gnome-en libsmbclient samba-common smbclient 
The following NEW packages will be installed:
  libgtkglext1 
The following partially installed packages will be configured:
  libgtkglext1-ruby libgtkglext1-ruby1.8 ruby-gnome2 
0 packages upgraded, 1 newly installed, 23 to remove and 6 not upgraded.
Need to get 0B/126kB of archives. After unpacking 18.4MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 139252 files and directories currently installed.)
Unpacking libgtkglext1 (from .../libgtkglext1_1.2.0-0ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libgdkglext-x11-1.0.so.0.0.0', which is also in package libgtkglext-1.0-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libgtkglext1-ruby1.8:
 libgtkglext1-ruby1.8 depends on libgtkglext1; however:
  Package libgtkglext1 is not installed.
dpkg: error processing libgtkglext1-ruby1.8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkglext1-ruby:
 libgtkglext1-ruby depends on libgtkglext1-ruby1.8; however:
  Package libgtkglext1-ruby1.8 is not configured yet.
dpkg: error processing libgtkglext1-ruby (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ruby-gnome2:
 ruby-gnome2 depends on libgtkglext1-ruby; however:
  Package libgtkglext1-ruby is not configured yet.
dpkg: error processing ruby-gnome2 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgtkglext1-ruby1.8
 libgtkglext1-ruby
 ruby-gnome2
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
maxtothemax@maxtothemax-desktop:~/alienarenainstalls/7.12/source$ 

```

---

### Post by pytheas22 on 2008-09-07
It doesn't look like it really did anything better than apt-get.  What about:
```

sudo aptitude remove --purge libgtkglext1-ruby1.8 libgtkglext1-ruby ruby-gnome2
```

It seems to be getting hung about on those three packages.  Hopefully we can tell it to just stop worrying about them.

---

### Post by MaxIBoy on 2008-09-07
Works now, thanks so much! Thanks to both people who gave advice, I'm marking this solved.

---

