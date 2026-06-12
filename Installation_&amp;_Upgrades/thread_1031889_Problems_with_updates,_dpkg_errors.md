---
title: "Problems with updates, dpkg errors"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by ben_l on 2009-01-05
When I run apt-get upgrade (or even when I use the Update Manager), I get errors like the ones below:

[INDENT]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common ghostscript ghostscript-x libcups2
  libcupsimage2 libgs8 libopal-2.2 libpulse-browse0 libpulse0 libpulsecore5
  libsmbclient libwbclient0 ntp ntpdate pulseaudio pulseaudio-esound-compat
  pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11
  pulseaudio-utils samba-common smbclient transmission-common transmission-gtk
  winbind xserver-xorg-video-ati xserver-xorg-video-radeon xterm
31 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 26.9MB of archives.
After this operation, 20.5kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main libwbclient0 2:3.2.3-1ubuntu3.4 [87.6kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main ntpdate 1:4.2.4p4+dfsg-6ubuntu2.1 [61.8kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main libsmbclient 2:3.2.3-1ubuntu3.4 [1218kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main libcups2 1.3.9-2ubuntu6 [169kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main libcupsimage2 1.3.9-2ubuntu6 [51.7kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main ghostscript 8.63.dfsg.1-0ubuntu6.1 [795kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main libgs8 8.63.dfsg.1-0ubuntu6.1 [2289kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main winbind 2:3.2.3-1ubuntu3.4 [2975kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main cups-common 1.3.9-2ubuntu6 [1162kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main smbclient 2:3.2.3-1ubuntu3.4 [6403kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main cups 1.3.9-2ubuntu6 [2139kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main cups-bsd 1.3.9-2ubuntu6 [36.2kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main cups-client 1.3.9-2ubuntu6 [115kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main ghostscript-x 8.63.dfsg.1-0ubuntu6.1 [62.6kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main libopal-2.2 2.2.11~dfsg1-4ubuntu1 [3114kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main samba-common 2:3.2.3-1ubuntu3.4 [3459kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main libpulse0 0.9.10-2ubuntu9.2 [145kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main libpulse-browse0 0.9.10-2ubuntu9.2 [24.2kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main libpulsecore5 0.9.10-2ubuntu9.2 [190kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main ntp 1:4.2.4p4+dfsg-6ubuntu2.1 [442kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main pulseaudio 0.9.10-2ubuntu9.2 [294kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main pulseaudio-esound-compat 0.9.10-2ubuntu9.2 [27.9kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main pulseaudio-module-gconf 0.9.10-2ubuntu9.2 [10.3kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main pulseaudio-module-hal 0.9.10-2ubuntu9.2 [15.8kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main pulseaudio-utils 0.9.10-2ubuntu9.2 [139kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main pulseaudio-module-x11 0.9.10-2ubuntu9.2 [16.8kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main transmission-gtk 1.34-0ubuntu2.2 [314kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main transmission-common 1.34-0ubuntu2.2 [143kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main xserver-xorg-video-radeon 1:6.9.0+git20081003.f9826a56-0ubuntu2.1 [394kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main xserver-xorg-video-ati 1:6.9.0+git20081003.f9826a56-0ubuntu2.1 [162kB]
Get:31 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main xterm 235-1ubuntu1.1 [471kB]
Fetched 26.9MB in 3min42s (121kB/s)                                            
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/ntpdate_1%3a4.2.4p4+dfsg-6ubuntu2.1_i386.deb (--unpack):
 files list file for package `libgii1-target-x' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/ntpdate_1%3a4.2.4p4+dfsg-6ubuntu2.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT]

I've found some references to this in other threads, but none of the fixes seem to work.  Any suggestions?  Any more info I can provide?

---

### Post by Partyboi2 on 2009-01-05
Have your tried moving libgii1-target-x.list out of the way and then reinstalling the package?
```
sudo mv /var/lib/dpkg/info/libgii1-target-x.list /var/lib/dpkg/info/libgii1-target-x.list.bak
``` then
```
sudo apt-get --reinstall install libgii1-target-x
```
then try upgrading again.

---

### Post by ben_l on 2009-01-06
I've tried moving that file, but when I do, I get the same error with a different package.

---

### Post by gettinoriginal on 2009-01-06
First:  System > Admin > Software Sources > Ubuntu Software, first 4 boxes should be checked, Updates, make sure all 4 top boxes are checked, check your choice for automatic (when and how), and then "release upgrade" , normal releases

Then run these two in terminal, one at a time:

```
 sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list 
```

```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update 
```

---

### Post by ben_l on 2009-01-06
I get pretty much the same thing.

> sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list
Password or swipe finger: 
--2009-01-06 18:11:13--  [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 230 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 230         --.-K/s   in 0s      

2009-01-06 18:11:13 (14.5 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [230/230]

ben@thinkpad:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
OK
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg                          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg [189B]                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release [44.0kB]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US         
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg [189B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                              
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release [51.2kB]           
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release [11.7kB]                  
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages [46.1kB]      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources                   
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages [269kB]      
Get:9 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages [3518B]             
Get:10 [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages [12.6kB]       
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages [1785B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources [14.4kB]    
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources [571B]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages [17.9kB] 
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources [2429B]   
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages [1330B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources [584B]  
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages [5049B]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources [83.2kB]     
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources [1696B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages [34.2kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources [6708B]  
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages [3180B]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources [1145B]
Fetched 613kB in 10s (57.7kB/s)                                                
Reading package lists... Done
ben@thinkpad:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                          
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release                              
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US              
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Sources                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Reading package lists... Done
ben@thinkpad:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  mplayer
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common ghostscript ghostscript-x libcups2
  libcupsimage2 libgs8 libopal-2.2 libpulse-browse0 libpulse0 libpulsecore5
  libsmbclient libwbclient0 ntp ntpdate nvidia-177-kernel-source
  nvidia-177-modaliases nvidia-glx-177 pulseaudio pulseaudio-esound-compat
  pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11
  pulseaudio-utils samba-common smbclient transmission-common transmission-gtk
  winbind xserver-xorg-video-ati xserver-xorg-video-radeon xterm
34 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 11.7MB/38.6MB of archives.
After this operation, 41.0kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted nvidia-177-kernel-source 177.82-0ubuntu0.1 [2713kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main nvidia-177-modaliases 177.82-0ubuntu0.1 [18.4kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted nvidia-glx-177 177.82-0ubuntu0.1 [8932kB]
Fetched 11.7MB in 1min30s (128kB/s)                                            
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/ntpdate_1%3a4.2.4p4+dfsg-6ubuntu2.1_i386.deb (--unpack):
 files list file for package `libgii1-target-x' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/ntpdate_1%3a4.2.4p4+dfsg-6ubuntu2.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
ben@thinkpad:~$ 



That's about where I was before.

---

### Post by Partyboi2 on 2009-01-06
> **ben_l said:**
> I've tried moving that file, but when I do, I get the same error with a different package.
Have you tried the same process with the different package?

---

### Post by ben_l on 2009-01-06
I have like 30 packages pending download.  I've tried renaming the lists file but it just goes on to another package.  Sometimes when I do the apt-get upgrade, it downloads the packages again, but it never installs anything.

---

### Post by mc4man on 2009-01-06
Have you tried updating from the update manager and unchecking some of the updates (ntp ntpdate for sure

---

### Post by Partyboi2 on 2009-01-06
You could try post #12 of [[COLOR=Blue]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=12737&page=2") thread.

---

### Post by ben_l on 2009-01-06
I'm not sure if I did this right, but I'm getting pretty much the same thing

> ben@thinkpad:~$ dpkg --contents /var/cache/apt/archives/ntpdate_1%3a4.2.4p4+dfsg-6ubuntu2.1_i386.deb
drwxr-xr-x root/root         0 2008-12-17 01:46 ./
drwxr-xr-x root/root         0 2008-12-17 01:46 ./etc/
drwxr-xr-x root/root         0 2008-12-17 01:46 ./etc/dhcp3/
drwxr-xr-x root/root         0 2008-12-17 01:46 ./etc/dhcp3/dhclient-exit-hooks.d/
-rw-r--r-- root/root       802 2008-12-17 01:46 ./etc/dhcp3/dhclient-exit-hooks.d/ntpdate
drwxr-xr-x root/root         0 2008-12-17 01:46 ./etc/default/
-rw-r--r-- root/root       456 2008-12-17 01:45 ./etc/default/ntpdate
drwxr-xr-x root/root         0 2008-12-17 01:46 ./etc/logcheck/
drwxr-xr-x root/root         0 2008-12-17 01:46 ./etc/logcheck/ignore.d.server/
-rw-r--r-- root/root       106 2008-12-17 01:46 ./etc/logcheck/ignore.d.server/ntpdate
drwxr-xr-x root/root         0 2008-12-17 01:46 ./etc/network/
drwxr-xr-x root/root         0 2008-12-17 01:46 ./etc/network/if-up.d/
-rwxr-xr-x root/root      1135 2008-12-17 01:45 ./etc/network/if-up.d/ntpdate
drwxr-xr-x root/root         0 2008-12-17 01:46 ./usr/
drwxr-xr-x root/root         0 2008-12-17 01:46 ./usr/sbin/
-rwxr-xr-x root/root       530 2008-12-17 01:46 ./usr/sbin/ntpdate-debian
-rwxr-xr-x root/root     49492 2008-12-17 01:46 ./usr/sbin/ntpdate
drwxr-xr-x root/root         0 2008-12-17 01:46 ./usr/share/
drwxr-xr-x root/root         0 2008-12-17 01:46 ./usr/share/doc/
drwxr-xr-x root/root         0 2008-12-17 01:46 ./usr/share/doc/ntpdate/
-rw-r--r-- root/root       759 2008-12-17 01:45 ./usr/share/doc/ntpdate/README.Debian
-rw-r--r-- root/root     22032 2008-12-17 01:45 ./usr/share/doc/ntpdate/copyright
-rw-r--r-- root/root      2006 2008-12-17 01:45 ./usr/share/doc/ntpdate/NEWS.Debian.gz
-rw-r--r-- root/root     21582 2008-12-17 01:45 ./usr/share/doc/ntpdate/changelog.Debian.gz
drwxr-xr-x root/root         0 2008-12-17 01:46 ./usr/share/man/
drwxr-xr-x root/root         0 2008-12-17 01:46 ./usr/share/man/man8/
-rw-r--r-- root/root      2476 2008-12-17 01:46 ./usr/share/man/man8/ntpdate.8.gz
-rw-r--r-- root/root       302 2008-12-17 01:46 ./usr/share/man/man8/ntpdate-debian.8.gz
ben@thinkpad:~$ sudo -i
root@thinkpad:~# 
root@thinkpad:~# dpkg -c  /var/cache/apt/archives/ntpdate_1%3a4.2.4p4+dfsg-6ubuntu2.1_i386.deb | awk '{if ($6 == "./"){ print "/."; } \
> else if (substr($6, length($6), 1) == "/")\
> {print substr($6, 2, length($6) - 2); } \
> else { print substr($6, 2, length($6) - 1);}}'\
> > /var/lib/dpkg/info/ntpdate.list
root@thinkpad:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  mplayer
The following packages will be upgraded:
  cups cups-bsd cups-client cups-common ghostscript ghostscript-x libcups2
  libcupsimage2 libgs8 libopal-2.2 libpulse-browse0 libpulse0 libpulsecore5
  libsmbclient libwbclient0 ntp ntpdate nvidia-177-kernel-source
  nvidia-177-modaliases nvidia-glx-177 pulseaudio pulseaudio-esound-compat
  pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11
  pulseaudio-utils samba-common smbclient transmission-common transmission-gtk
  winbind xserver-xorg-video-ati xserver-xorg-video-radeon xterm
34 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/38.6MB of archives.
After this operation, 41.0kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/ntpdate_1%3a4.2.4p4+dfsg-6ubuntu2.1_i386.deb (--unpack):
 files list file for package `libgii1-target-x' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/ntpdate_1%3a4.2.4p4+dfsg-6ubuntu2.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@thinkpad:~# 



---

### Post by gettinoriginal on 2009-01-07
Check synaptic to be sure that  libgii1-target-x is installed, and even if it is , right click to reinstall.

---

### Post by ben_l on 2009-01-09
I try that and get the error:

> E: /var/cache/apt/archives/libgii1-target-x_1%3a1.0.2-2_i386.deb: files list file for package `libgii1-target-x' contains empty filename

Everything I see online where people are able to fix it, I've tried and non of it works.  :confused:

---

### Post by ben_l on 2009-01-09
I got it fixed!  I had to go into /var/lib/dpkg/info and move packagename.* one at a time, into a temp directory I created.  After moving files for each package, I tried apt-get upgrade, until it ran successfully.  Apparently I just wasn't patient enough to move the files.  !!!

---

