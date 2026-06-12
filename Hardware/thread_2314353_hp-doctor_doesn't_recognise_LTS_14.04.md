---
title: "hp-doctor doesn't recognise LTS 14.04"
date: 2016-02-20
forum: Hardware
---

### Post by engine on 2016-02-20
Lubuntu 14.04
synaptic reports hplip 3.14.3-0ubuntu3.4 as installed version
hp-doctor says "this distro is either deprecated or not yet supported"
Do I need a newer hplip? and if so, how do I go about getting it?

---

### Post by mörgæs on 2016-02-21
Which printer are you using?

---

### Post by engine on 2016-02-22
HP Deskjet 840C &#8210; prints quite happily apart from .pdf, and this is a new problem.

---

### Post by mörgæs on 2016-02-22
It seems that the printer has been well supported for quite some time: 

[http://hplipopensource.com/hplip-web/models/deskjet/deskjet_840c.html](http://hplipopensource.com/hplip-web/models/deskjet/deskjet_840c.html)

If you want to try a new hplip you can download it from the page. A PPA might also be available but I haven't seen it.

---

### Post by engine on 2016-02-23
not going so well &#8230; the installer identifies libcupsimage2-dev as a required package it can't install itself; I go to synaptic, select libcupsimage2-dev for installation and am immediately told there is "a broken package". It doesn't tell me which one, and it doesn't tell me why it's proposing to install it. Any hints on how to resolve this new challenge?

---

### Post by mörgæs on 2016-02-23
Please post the output from ```
sudo apt-get update
``` and ```
sudo apt-get dist-upgrade
``` in CODE tags. 
Read carefully the messages which might come up.

---

### Post by engine on 2016-02-28
Thanks for replying! I'm baffled and out of my comfort zone here &#8230; I sha'n't try upgrading libcupsimage2-dev until you've scrutinised the outputs you asked for and given me more instructions :-}

```
Ign http://extras.ubuntu.com trusty InRelease
Hit http://files.eid.belgium.be trusty InRelease                               
Ign http://archive.canonical.com trusty InRelease                              
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:1 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.canonical.com trusty Release                                
Ign http://archive.ubuntu.com trusty InRelease                          
Get:2 http://archive.ubuntu.com trusty-updates InRelease [65.9 kB]             
Hit http://files.eid.belgium.be trusty/main i386 Packages                      
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://archive.canonical.com trusty/partner Translation-en                 
Get:3 http://archive.ubuntu.com trusty-backports InRelease [65.9 kB]           
Get:4 http://archive.ubuntu.com trusty-security InRelease [65.9 kB]            
Ign http://ppa.launchpad.net trusty/main Translation-en_GB                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://files.eid.belgium.be trusty/main Translation-en_GB         
Hit http://archive.ubuntu.com trusty Release.gpg                      
Ign http://extras.ubuntu.com trusty/main Translation-en_GB
Ign http://files.eid.belgium.be trusty/main Translation-en
Ign http://extras.ubuntu.com trusty/main Translation-en
Ign http://files.eid.belgium.be trusty/main Translation-en_US
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Get:5 http://archive.ubuntu.com trusty-updates/main Sources [260 kB]
Get:6 http://archive.ubuntu.com trusty-updates/restricted Sources [5,352 B]
Get:7 http://archive.ubuntu.com trusty-updates/universe Sources [150 kB]
Get:8 http://archive.ubuntu.com trusty-updates/multiverse Sources [5,547 B]
Get:9 http://archive.ubuntu.com trusty-updates/main i386 Packages [689 kB]
Get:10 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:11 http://archive.ubuntu.com trusty-updates/universe i386 Packages [339 kB]
Get:12 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [13.4 kB]
Get:13 http://archive.ubuntu.com trusty-updates/main Translation-en [359 kB]
Get:14 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [6,947 B]
Get:15 http://archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:16 http://archive.ubuntu.com trusty-updates/universe Translation-en [180 kB]
Get:17 http://archive.ubuntu.com trusty-backports/main Sources [8,661 B]
Get:18 http://archive.ubuntu.com trusty-backports/restricted Sources [28 B]
Get:19 http://archive.ubuntu.com trusty-backports/universe Sources [33.2 kB]
Get:20 http://archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:21 http://archive.ubuntu.com trusty-backports/main i386 Packages [9,814 B]
Get:22 http://archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:23 http://archive.ubuntu.com trusty-backports/universe i386 Packages [40.0 kB]
Get:24 http://archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Hit http://archive.ubuntu.com trusty-backports/main Translation-en
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en
Get:25 http://archive.ubuntu.com trusty-security/main Sources [105 kB]
Get:26 http://archive.ubuntu.com trusty-security/restricted Sources [4,035 B]
Get:27 http://archive.ubuntu.com trusty-security/universe Sources [33.0 kB]
Get:28 http://archive.ubuntu.com trusty-security/multiverse Sources [2,767 B]
Get:29 http://archive.ubuntu.com trusty-security/main i386 Packages [399 kB]
Get:30 http://archive.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Get:31 http://archive.ubuntu.com trusty-security/universe i386 Packages [124 kB]
Get:32 http://archive.ubuntu.com trusty-security/multiverse i386 Packages [5,164 B]
Get:33 http://archive.ubuntu.com trusty-security/main Translation-en [234 kB]
Get:34 http://archive.ubuntu.com trusty-security/multiverse Translation-en [2,570 B]
Get:35 http://archive.ubuntu.com trusty-security/restricted Translation-en [3,206 B]
Get:36 http://archive.ubuntu.com trusty-security/universe Translation-en [72.6 kB]
Hit http://archive.ubuntu.com trusty Release                                   
Hit http://archive.ubuntu.com trusty/main Sources                              
Hit http://archive.ubuntu.com trusty/restricted Sources                        
Hit http://archive.ubuntu.com trusty/universe Sources                          
Hit http://archive.ubuntu.com trusty/multiverse Sources                        
Hit http://archive.ubuntu.com trusty/main i386 Packages                        
Hit http://archive.ubuntu.com trusty/restricted i386 Packages                  
Hit http://archive.ubuntu.com trusty/universe i386 Packages                    
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages                  
Hit http://archive.ubuntu.com trusty/main Translation-en_GB                    
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://archive.ubuntu.com trusty/multiverse Translation-en_GB              
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                 
Hit http://archive.ubuntu.com trusty/restricted Translation-en_GB              
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Hit http://archive.ubuntu.com trusty/universe Translation-en_GB                
Hit http://archive.ubuntu.com trusty/universe Translation-en                   
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Fetched 3,319 kB in 13s (251 kB/s)                                             
Reading package lists... Done
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  catdoc libphp-adodb libzend-framework-php linux-headers-3.13.0-24
  linux-headers-3.13.0-24-generic linux-image-3.13.0-24-generic
  linux-image-extra-3.13.0-24-generic php-auth-sasl php-db php-log php-mail
  php-mdb2 php-net-smtp php-net-socket php5-sqlite zend-framework
  zend-framework-bin
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  gcc-4.9-base libgcc1
The following packages will be upgraded:
  gir1.2-gtk-3.0 libgail-3-0 libgtk-3-0 libgtk-3-bin libgtk-3-common
  libmm-glib0 libnautilus-extension1a modemmanager nautilus-data oneconf
  oneconf-common python-oneconf python3-oneconf
13 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.
Need to get 3,055 kB of archives.
After this operation, 111 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk-3-common all 3.10.8-0ubuntu1.6 [167 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libgail-3-0 i386 3.10.8-0ubuntu1.6 [20.1 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk-3-0 i386 3.10.8-0ubuntu1.6 [1,923 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libmm-glib0 i386 1.0.0-2ubuntu1.1 [127 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty-updates/main gir1.2-gtk-3.0 i386 3.10.8-0ubuntu1.6 [174 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libgtk-3-bin i386 3.10.8-0ubuntu1.6 [18.0 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libnautilus-extension1a i386 1:3.10.1-0ubuntu9.11 [51.9 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ trusty-updates/main modemmanager i386 1.0.0-2ubuntu1.1 [473 kB]
Get:9 http://archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus-data all 1:3.10.1-0ubuntu9.11 [50.7 kB]
Get:10 http://archive.ubuntu.com/ubuntu/ trusty-updates/main oneconf-common all 0.3.7.14.04.1 [6,042 B]
Get:11 http://archive.ubuntu.com/ubuntu/ trusty-updates/main python3-oneconf all 0.3.7.14.04.1 [19.5 kB]
Get:12 http://archive.ubuntu.com/ubuntu/ trusty-updates/main oneconf all 0.3.7.14.04.1 [5,458 B]
Get:13 http://archive.ubuntu.com/ubuntu/ trusty-updates/main python-oneconf all 0.3.7.14.04.1 [19.7 kB]
Fetched 3,055 kB in 1s (1,539 kB/s)   
(Reading database ... 1174406 files and directories currently installed.)
Preparing to unpack .../libgtk-3-common_3.10.8-0ubuntu1.6_all.deb ...
Unpacking libgtk-3-common (3.10.8-0ubuntu1.6) over (3.10.8-0ubuntu1.4) ...
Preparing to unpack .../libgail-3-0_3.10.8-0ubuntu1.6_i386.deb ...
Unpacking libgail-3-0:i386 (3.10.8-0ubuntu1.6) over (3.10.8-0ubuntu1.4) ...
Preparing to unpack .../libgtk-3-0_3.10.8-0ubuntu1.6_i386.deb ...
Unpacking libgtk-3-0:i386 (3.10.8-0ubuntu1.6) over (3.10.8-0ubuntu1.4) ...
Preparing to unpack .../libmm-glib0_1.0.0-2ubuntu1.1_i386.deb ...
Unpacking libmm-glib0:i386 (1.0.0-2ubuntu1.1) over (1.0.0-2ubuntu1) ...
Preparing to unpack .../gir1.2-gtk-3.0_3.10.8-0ubuntu1.6_i386.deb ...
Unpacking gir1.2-gtk-3.0 (3.10.8-0ubuntu1.6) over (3.10.8-0ubuntu1.4) ...
Preparing to unpack .../libgtk-3-bin_3.10.8-0ubuntu1.6_i386.deb ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking libgtk-3-bin (3.10.8-0ubuntu1.6) over (3.10.8-0ubuntu1.4) ...
Preparing to unpack .../libnautilus-extension1a_1%3a3.10.1-0ubuntu9.11_i386.deb ...
Unpacking libnautilus-extension1a (1:3.10.1-0ubuntu9.11) over (1:3.10.1-0ubuntu9.10) ...
Preparing to unpack .../modemmanager_1.0.0-2ubuntu1.1_i386.deb ...
modemmanager stop/waiting
Unpacking modemmanager (1.0.0-2ubuntu1.1) over (1.0.0-2ubuntu1) ...
Preparing to unpack .../nautilus-data_1%3a3.10.1-0ubuntu9.11_all.deb ...
Unpacking nautilus-data (1:3.10.1-0ubuntu9.11) over (1:3.10.1-0ubuntu9.10) ...
Preparing to unpack .../oneconf-common_0.3.7.14.04.1_all.deb ...
Unpacking oneconf-common (0.3.7.14.04.1) over (0.3.7) ...
Preparing to unpack .../python3-oneconf_0.3.7.14.04.1_all.deb ...
Unpacking python3-oneconf (0.3.7.14.04.1) over (0.3.7) ...
Preparing to unpack .../oneconf_0.3.7.14.04.1_all.deb ...
Unpacking oneconf (0.3.7.14.04.1) over (0.3.7) ...
Preparing to unpack .../python-oneconf_0.3.7.14.04.1_all.deb ...
Unpacking python-oneconf (0.3.7.14.04.1) over (0.3.7) ...
Processing triggers for libglib2.0-0:i386 (2.42.1-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up libgtk-3-common (3.10.8-0ubuntu1.6) ...
Setting up libgtk-3-0:i386 (3.10.8-0ubuntu1.6) ...
Setting up libgail-3-0:i386 (3.10.8-0ubuntu1.6) ...
Setting up libmm-glib0:i386 (1.0.0-2ubuntu1.1) ...
Setting up gir1.2-gtk-3.0 (3.10.8-0ubuntu1.6) ...
Setting up libgtk-3-bin (3.10.8-0ubuntu1.6) ...
Setting up libnautilus-extension1a (1:3.10.1-0ubuntu9.11) ...
Setting up modemmanager (1.0.0-2ubuntu1.1) ...
modemmanager start/running, process 3545
Setting up nautilus-data (1:3.10.1-0ubuntu9.11) ...
Setting up oneconf-common (0.3.7.14.04.1) ...
Setting up python3-oneconf (0.3.7.14.04.1) ...
Setting up oneconf (0.3.7.14.04.1) ...
Setting up python-oneconf (0.3.7.14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.7) ...
```

---

### Post by mörgæs on 2016-03-01
Thanks for the trust. I'm not sure I can live up to it, though. 

There are some strange observations in the output. Please run the two commands again and post the new output. Are there any changes?

---

### Post by engine on 2016-12-02
After upgrading to 16.04, I managed to print a couple of .pdf straight off. Now, however, the problem has come back.

hplip appears to be installed correctly:

```
me@myPC:~$ dpkg -l hplip
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version        Architecture   Description
+++-===================-==============-==============-============================================
ii  hplip               3.16.3+repack0 i386           HP Linux Printing and Imaging System (HPLIP)
```

So far so good. But the HP site says ```
Configure your printer using hp-setup
```, and when I try that I get less encouraging messages:

```
me@myPC:~$ sudo hp-setup

HP Linux Imaging and Printing System (ver. 3.16.3)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-15 HP Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

error: HPLIP is not installed properly or is installed without graphical support. Please reinstall HPLIP
warning: Qt/PyQt 4 initialization failed.
error: hp-setup requires GUI support (try running with --qt3). Also, try using interactive (-i) mode.
```

Now, how do I sort out this new problem so I stand some chance of running hp-setup?

---

### Post by mörgæs on 2016-12-03
Was it a fresh install of 16.04 or an upgrade in-place?

---

### Post by engine on 2016-12-04
upgrade in place

---

### Post by mörgæs on 2016-12-05
If you have fought with this problem since February I recommend trying a fresh install.

---

