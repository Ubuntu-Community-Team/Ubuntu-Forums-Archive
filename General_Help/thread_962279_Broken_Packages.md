---
title: "Broken Packages"
date: 2008-10-29
forum: General Help
---

### Post by freeqaz on 2008-10-29
```
root@free-desktop:~# apt-get purge mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  aqualung libavformat1d libavutil1d libenca0 libpostproc1d mplayer
0 upgraded, 0 newly installed, 6 to remove and 17 not upgraded.
32 not fully installed or removed.
After this operation, 13.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 100596 files and directories currently installed.)
Removing aqualung ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing aqualung (--remove):
 subprocess post-removal script returned error exit status 2
Removing libavformat1d ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libavformat1d (--remove):
 subprocess post-removal script returned error exit status 2
Removing libpostproc1d ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libpostproc1d (--remove):
 subprocess post-removal script returned error exit status 2
Removing libavutil1d ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libavutil1d (--remove):
 subprocess post-removal script returned error exit status 2
Removing mplayer ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing mplayer (--remove):
 subprocess post-removal script returned error exit status 2
Removing libenca0 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libenca0 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 aqualung
 libavformat1d
 libpostproc1d
 libavutil1d
 mplayer
 libenca0
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@free-desktop:~# 
```

This is the error that I get when I try to install any packages, or remove any packages. My computer had a power outage durring an install of apps, and it broke everything. Any ideas on fixing it? I've tried apt-get purge * as you see. Can't install Flash Player or Wine so my install is dead right now. :(

---

### Post by bapoumba on 2008-10-29
Please try :
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Hopefully, it will complete and finish the update you were doing when power went out.
if not, please post the error output.

---

### Post by freeqaz on 2008-10-30
```
root@free-desktop:~# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  aqualung libavformat1d
The following NEW packages will be installed:
  libdns35 libisc35 linux-headers-2.6.24-21 linux-headers-2.6.24-21-generic
  linux-image-2.6.24-21-generic linux-restricted-modules-2.6.24-21-generic
  linux-ubuntu-modules-2.6.24-21-generic openssl-blacklist
The following packages will be upgraded:
  apt apt-utils bind9-host dnsutils gtk2-engines-pixbuf libbind9-30
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libisccc30 libisccfg30
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic ssl-cert thunderbird-locale-en-gb tzdata
  xkb-data xserver-xorg-video-intel
20 upgraded, 8 newly installed, 2 to remove and 0 not upgraded.
32 not fully installed or removed.
Need to get 64.7MB/69.2MB of archives.
After this operation, 208MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hardy-updates/main libgtk2.0-common 2.12.9-3ubuntu5 [304kB]
Get:2 http://us.archive.ubuntu.com hardy-updates/main gtk2-engines-pixbuf 2.12.9-3ubuntu5 [317kB]
Get:3 http://us.archive.ubuntu.com hardy-updates/main libgtk2.0-0 2.12.9-3ubuntu5 [2068kB]
Get:4 http://us.archive.ubuntu.com hardy-updates/main linux-image-2.6.24-21-generic 2.6.24-21.43 [18.4MB]
Get:5 http://us.archive.ubuntu.com hardy-updates/main linux-ubuntu-modules-2.6.24-21-generic 2.6.24-21.32 [5429kB]
Get:6 http://us.archive.ubuntu.com hardy-updates/main openssl-blacklist 0.3.3+0.4-0ubuntu0.8.04.3 [6333kB]
Get:7 http://us.archive.ubuntu.com hardy-updates/main apt 0.7.9ubuntu17.1 [1650kB]
Get:8 http://us.archive.ubuntu.com hardy-updates/main tzdata 2008h-0ubuntu0.8.04.1 [659kB]
Get:9 http://us.archive.ubuntu.com hardy-updates/main apt-utils 0.7.9ubuntu17.1 [200kB]
Get:10 http://us.archive.ubuntu.com hardy-updates/main xkb-data 1.1~cvs.20080104.1-1ubuntu8 [341kB]
Get:11 http://us.archive.ubuntu.com hardy-updates/main libisc35 1:9.4.2.dfsg.P2-2 [127kB]
Get:12 http://us.archive.ubuntu.com hardy-updates/main libdns35 1:9.4.2.dfsg.P2-2 [494kB]
Get:13 http://us.archive.ubuntu.com hardy-updates/main libisccc30 1:9.4.2.dfsg.P2-2 [23.1kB]
Get:14 http://us.archive.ubuntu.com hardy-updates/main libisccfg30 1:9.4.2.dfsg.P2-2 [38.5kB]
Get:15 http://us.archive.ubuntu.com hardy-updates/main libbind9-30 1:9.4.2.dfsg.P2-2 [27.5kB]
Get:16 http://us.archive.ubuntu.com hardy-updates/main bind9-host 1:9.4.2.dfsg.P2-2 [56.7kB]
Get:17 http://us.archive.ubuntu.com hardy-updates/main dnsutils 1:9.4.2.dfsg.P2-2 [135kB]
Get:18 http://us.archive.ubuntu.com hardy-updates/main libgtk2.0-bin 2.12.9-3ubuntu5 [137kB]
Get:19 http://us.archive.ubuntu.com hardy-updates/restricted linux-generic 2.6.24.21.23 [26.5kB]
Get:20 http://us.archive.ubuntu.com hardy-updates/main linux-image-generic 2.6.24.21.23 [26.5kB]
Get:21 http://us.archive.ubuntu.com hardy-updates/restricted linux-restricted-modules-2.6.24-21-generic 2.6.24.14-21.51 [18.6MB]
Get:22 http://us.archive.ubuntu.com hardy-updates/restricted linux-restricted-modules-generic 2.6.24.21.23 [26.5kB]
Get:23 http://us.archive.ubuntu.com hardy-updates/main linux-headers-2.6.24-21 2.6.24-21.43 [8134kB]
Get:24 http://us.archive.ubuntu.com hardy-updates/main linux-headers-2.6.24-21-generic 2.6.24-21.43 [648kB]
Get:25 http://us.archive.ubuntu.com hardy-updates/main linux-headers-generic 2.6.24.21.23 [26.5kB]
Get:26 http://us.archive.ubuntu.com hardy-updates/main ssl-cert 1.0.14-0ubuntu2.1 [12.3kB]
Get:27 http://us.archive.ubuntu.com hardy-updates/main thunderbird-locale-en-gb 1:2.0.0.14+1-0ubuntu1~8.04.1 [184kB]
Get:28 http://us.archive.ubuntu.com hardy-updates/main xserver-xorg-video-intel 2:2.2.1-1ubuntu13.7 [336kB]
Fetched 64.7MB in 3min57s (272kB/s)                                            
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 100596 files and directories currently installed.)
Removing aqualung ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing aqualung (--remove):
 subprocess post-removal script returned error exit status 2
Removing libavformat1d ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libavformat1d (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 aqualung
 libavformat1d
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

That's what I got now. Seems to have purged out some of those errors though. :P What now?

---

### Post by freeqaz on 2008-10-30
:(

---

### Post by DougieFresh4U on 2008-10-30
Maybe try
```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by freeqaz on 2008-10-31
```
root@free-desktop:~# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libglide2 (2002.04.10-15ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libglide2 (--configure):
 subprocess post-installation script returned error exit status 2
Setting up ttf-dejavu-extra (2.23-1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing ttf-dejavu-extra (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 libglide2
 ttf-dejavu-extra
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
 /wrists

---

### Post by bapoumba on 2008-11-01
[http://ubuntuforums.org/showthread.php?t=401232](http://ubuntuforums.org/showthread.php?t=401232)

There may be a solution in the linked thread. Please try it on the two packages that have postinst corrupt scripts (ie : libglide2 and ttf-dejavu-extra).

---

### Post by grimey44 on 2008-12-04
Ive got a similar problem while trying to instal flash.
this is the error code i get:


```
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2) intrepid/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release.gpg                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Translation-en_US         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid Release                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/multiverse Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/multiverse Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/main Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid-updates/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu:~$ sudo apt-get dist-upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

I have no idea how to fix this.

---

### Post by bapoumba on 2008-12-04
@ grimey44: would you have synaptic or another package manager open while trying to install the package? If so, please close it first.

---

### Post by grimey44 on 2008-12-04
I closed it and try again but still wont.

i tried installing it in synaptic package manager and it said:

the following packages haveunresolved dependencies. Make sure all required repositories are added and enabled in the preferences.

```

flashplugin-nonfree:
 Depends: nspluginwrapper but it is not going to be installed

```

not sure what to try next.

---

### Post by bapoumba on 2008-12-04
> **grimey44 said:**
> I closed it and try again but still wont.

i tried installing it in synaptic package manager and it said:

the following packages haveunresolved dependencies. Make sure all required repositories are added and enabled in the preferences.

```

flashplugin-nonfree:
 Depends: nspluginwrapper but it is not going to be installed

```

not sure what to try next.
Do you have the multiverse repositories enabled ?

---

### Post by grimey44 on 2008-12-04
i have enabled the multiverse 
and then tried installing it again, and it downloaded everything and looked like it was working, then after all was done, it jsut said it failed.

---

### Post by bapoumba on 2008-12-04
> **grimey44 said:**
> i have enabled the multiverse 
and then tried installing it again, and it downloaded everything and looked like it was working, then after all was done, it jsut said it failed.
After enabling multiverse, did you reload the file (hit the reload button from synaptic for ex, or run **sudo apt-get update**) before trying to install flash ?

Have you installed ubuntu-restricted-extras ? Many useful restricted packages are in this meta-package.
[http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras](http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras)

---

