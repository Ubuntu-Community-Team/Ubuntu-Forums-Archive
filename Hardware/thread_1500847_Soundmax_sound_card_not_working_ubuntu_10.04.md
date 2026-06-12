---
title: "Soundmax sound card not working: ubuntu 10.04"
date: 2010-06-03
forum: Hardware
---

### Post by joggleh on 2010-06-03
First of all: I like that little search bar in the top right corner of the screen, it's just that there didn't seem any solution for my problem in the treads listed.

I've installed ubuntu 10.04 just fine, except for the fact my sound isn't working. Ubuntu doesn't seem to recognise my soundmax digital audio soundcard at all (tried the command that was in the sound troubleshooting guide). In my crappy windows XP install, the sound works like a charm, so it's definitely not a hardware problem. 

Any suggestions? By the way, I use a desktop computer, not a laptop.

---

### Post by joggleh on 2010-06-07
Bump.

Come on guys, an OS without sound is so frustrating...

---

### Post by lidex on 2010-06-09
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by joggleh on 2010-06-16
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

uname -a:

```
Linux joris-desktop 2.6.32-22-generic-pae #36-Ubuntu SMP Thu Jun 3 23:14:23 UTC 2010 i686 GNU/Linux

```

aplay -l

```
aplay: device_list:223: no soundcards found...
```

cat /proc/asound/version

```
Advanced Linux Sound Architecture Driver Version 1.0.21.

```

head -n 1 /proc/asound/card*/codec#*

```
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

```

Sorry for the late reply.

---

### Post by lidex on 2010-06-16
Try this.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.
Then
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
**Reboot.**

Now this output:
```
aplay -l
```

---

### Post by joggleh on 2010-06-17
Hold your breath...

```
joris@joris-desktop:~$ sudo apt-get update
[sudo] password for joris: 
diekoe8Sorry, try again.
[sudo] password for joris: 
Sorry, try again.
[sudo] password for joris: 
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ lucid/partner Translation-en_US              
Hit http://nl.archive.ubuntu.com lucid Release.gpg                             
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release.gpg            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Get:1 http://ppa.launchpad.net lucid Release.gpg [307B]                        
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Get:2 http://nl.archive.ubuntu.com lucid-updates Release.gpg [189B]            
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://archive.canonical.com lucid Release                                 
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://nl.archive.ubuntu.com lucid Release                                 
Get:3 http://ppa.launchpad.net lucid Release [57.3kB]                          
Get:4 http://nl.archive.ubuntu.com lucid-updates Release [44.7kB]              
Hit http://archive.canonical.com lucid Release                                 
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources                     
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://security.ubuntu.com lucid-security/universe Sources                 
Hit http://security.ubuntu.com lucid-security/multiverse Packages      
Hit http://security.ubuntu.com lucid-security/multiverse Sources       
Hit http://nl.archive.ubuntu.com lucid/main Packages                   
Hit http://nl.archive.ubuntu.com lucid/restricted Packages
Hit http://nl.archive.ubuntu.com lucid/main Sources
Hit http://nl.archive.ubuntu.com lucid/restricted Sources
Hit http://nl.archive.ubuntu.com lucid/universe Packages
Hit http://nl.archive.ubuntu.com lucid/universe Sources
Get:5 http://ppa.launchpad.net lucid/main Packages [2,766B]
Hit http://nl.archive.ubuntu.com lucid/multiverse Packages
Hit http://nl.archive.ubuntu.com lucid/multiverse Sources
Get:6 http://nl.archive.ubuntu.com lucid-updates/main Packages [224kB]
Get:7 http://nl.archive.ubuntu.com lucid-updates/restricted Packages [3,252B]
Get:8 http://nl.archive.ubuntu.com lucid-updates/main Sources [82.1kB]
Get:9 http://nl.archive.ubuntu.com lucid-updates/restricted Sources [1,292B]
Get:10 http://nl.archive.ubuntu.com lucid-updates/universe Packages [52.2kB]
Get:11 http://nl.archive.ubuntu.com lucid-updates/universe Sources [14.8kB]
Get:12 http://nl.archive.ubuntu.com lucid-updates/multiverse Packages [3,459B]
Get:13 http://nl.archive.ubuntu.com lucid-updates/multiverse Sources [1,532B]
Fetched 488kB in 3s (140kB/s)                            
Reading package lists... Done
joris@joris-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  gparted
The following packages will be upgraded:
  evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-plugins fglrx-modaliases
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio libcamel1.2-14
  libebackend1.2-0 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserver1.2-11 libedataserverui1.2-8
  libegroupwise1.2-13 libexchange-storage1.2-3 libgdata-google1.2-1
  libgdata1.2-1 libgssapi-krb5-2 libido-0.1-0 libk5crypto3 libkrb5-3
  libkrb5support0 libsdl1.2debian libsdl1.2debian-pulseaudio
  nvidia-185-modaliases nvidia-current-modaliases software-center
  telepathy-butterfly udisks xserver-common xserver-xorg-core
34 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 13.1MB of archives.
After this operation, 8,192B disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libk5crypto3 1.8.1+dfsg-2ubuntu0.1 [96.2kB]
Get:2 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.1 [120kB]
Get:3 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libkrb5-3 1.8.1+dfsg-2ubuntu0.1 [350kB]
Get:4 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libkrb5support0 1.8.1+dfsg-2ubuntu0.1 [42.2kB]
Get:5 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libedataserver1.2-11 2.28.3.1-0ubuntu3 [128kB]
Get:6 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libcamel1.2-14 2.28.3.1-0ubuntu3 [357kB]
Get:7 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libebackend1.2-0 2.28.3.1-0ubuntu3 [15.5kB]
Get:8 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libebook1.2-9 2.28.3.1-0ubuntu3 [80.8kB]
Get:9 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libecal1.2-7 2.28.3.1-0ubuntu3 [103kB]
Get:10 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libedata-book1.2-2 2.28.3.1-0ubuntu3 [49.8kB]
Get:11 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libedata-cal1.2-6 2.28.3.1-0ubuntu3 [66.9kB]
Get:12 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libegroupwise1.2-13 2.28.3.1-0ubuntu3 [67.8kB]
Get:13 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libgdata1.2-1 2.28.3.1-0ubuntu3 [76.6kB]
Get:14 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libgdata-google1.2-1 2.28.3.1-0ubuntu3 [13.4kB]
Get:15 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main evolution-data-server 2.28.3.1-0ubuntu3 [489kB]
Get:16 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main evolution-data-server-common 2.28.3.1-0ubuntu3 [87.1kB]
Get:17 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libedataserverui1.2-8 2.28.3.1-0ubuntu3 [87.4kB]
Get:18 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libexchange-storage1.2-3 2.28.3.1-0ubuntu3 [120kB]
Get:19 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main evolution 2.28.3-0ubuntu10 [2,427kB]
Get:20 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main evolution-common 2.28.3-0ubuntu10 [3,234kB]
Get:21 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main evolution-plugins 2.28.3-0ubuntu10 [223kB]
Get:22 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main gstreamer0.10-plugins-good 0.10.21-1ubuntu3 [1,433kB]
Get:23 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main gstreamer0.10-pulseaudio 0.10.21-1ubuntu3 [88.7kB]
Get:24 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libido-0.1-0 0.1.6-0ubuntu1 [10.4kB]
Get:25 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libsdl1.2debian 1.2.14-4ubuntu1.1 [23.3kB]
Get:26 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main libsdl1.2debian-pulseaudio 1.2.14-4ubuntu1.1 [204kB]
Get:27 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main nvidia-current-modaliases 195.36.24-0ubuntu1~10.04 [21.2kB]
Get:28 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main nvidia-185-modaliases 195.36.24-0ubuntu1~10.04 [4,506B]
Get:29 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main software-center 2.0.5 [279kB]
Get:30 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main telepathy-butterfly 0.5.11-0ubuntu1 [49.3kB]
Get:31 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main udisks 1.0.1-1ubuntu1 [212kB]
Get:32 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main xserver-common 2:1.7.6-2ubuntu7.1 [83.3kB]
Get:33 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main xserver-xorg-core 2:1.7.6-2ubuntu7.1 [2,409kB]
Get:34 http://nl.archive.ubuntu.com/ubuntu/ lucid-updates/main fglrx-modaliases 2:8.723.1-0ubuntu4 [15.0kB]
Fetched 13.1MB in 1min 20s (162kB/s)                                           
Extracting templates from packages: 100%
(Reading database ... 149618 files and directories currently installed.)
Preparing to replace libk5crypto3 1.8.1+dfsg-2 (using .../libk5crypto3_1.8.1+dfsg-2ubuntu0.1_i386.deb) ...
Unpacking replacement libk5crypto3 ...
Preparing to replace libgssapi-krb5-2 1.8.1+dfsg-2 (using .../libgssapi-krb5-2_1.8.1+dfsg-2ubuntu0.1_i386.deb) ...
Unpacking replacement libgssapi-krb5-2 ...
Preparing to replace libkrb5-3 1.8.1+dfsg-2 (using .../libkrb5-3_1.8.1+dfsg-2ubuntu0.1_i386.deb) ...
Unpacking replacement libkrb5-3 ...
Preparing to replace libkrb5support0 1.8.1+dfsg-2 (using .../libkrb5support0_1.8.1+dfsg-2ubuntu0.1_i386.deb) ...
Unpacking replacement libkrb5support0 ...
Preparing to replace libedataserver1.2-11 2.28.3.1-0ubuntu2 (using .../libedataserver1.2-11_2.28.3.1-0ubuntu3_i386.deb) ...
Unpacking replacement libedataserver1.2-11 ...
Preparing to replace libcamel1.2-14 2.28.3.1-0ubuntu2 (using .../libcamel1.2-14_2.28.3.1-0ubuntu3_i386.deb) ...
Unpacking replacement libcamel1.2-14 ...
Preparing to replace libebackend1.2-0 2.28.3.1-0ubuntu2 (using .../libebackend1.2-0_2.28.3.1-0ubuntu3_i386.deb) ...
Unpacking replacement libebackend1.2-0 ...
Preparing to replace libebook1.2-9 2.28.3.1-0ubuntu2 (using .../libebook1.2-9_2.28.3.1-0ubuntu3_i386.deb) ...
Unpacking replacement libebook1.2-9 ...
Preparing to replace libecal1.2-7 2.28.3.1-0ubuntu2 (using .../libecal1.2-7_2.28.3.1-0ubuntu3_i386.deb) ...
Unpacking replacement libecal1.2-7 ...
Preparing to replace libedata-book1.2-2 2.28.3.1-0ubuntu2 (using .../libedata-book1.2-2_2.28.3.1-0ubuntu3_i386.deb) ...
Unpacking replacement libedata-book1.2-2 ...
Preparing to replace libedata-cal1.2-6 2.28.3.1-0ubuntu2 (using .../libedata-cal1.2-6_2.28.3.1-0ubuntu3_i386.deb) ...
Unpacking replacement libedata-cal1.2-6 ...
Preparing to replace libegroupwise1.2-13 2.28.3.1-0ubuntu2 (using .../libegroupwise1.2-13_2.28.3.1-0ubuntu3_i386.deb) ...
Unpacking replacement libegroupwise1.2-13 ...
Preparing to replace libgdata1.2-1 2.28.3.1-0ubuntu2 (using .../libgdata1.2-1_2.28.3.1-0ubuntu3_i386.deb) ...
Unpacking replacement libgdata1.2-1 ...
Preparing to replace libgdata-google1.2-1 2.28.3.1-0ubuntu2 (using .../libgdata-google1.2-1_2.28.3.1-0ubuntu3_i386.deb) ...
Unpacking replacement libgdata-google1.2-1 ...
Preparing to replace evolution-data-server 2.28.3.1-0ubuntu2 (using .../evolution-data-server_2.28.3.1-0ubuntu3_i386.deb) ...
Unpacking replacement evolution-data-server ...
Preparing to replace evolution-data-server-common 2.28.3.1-0ubuntu2 (using .../evolution-data-server-common_2.28.3.1-0ubuntu3_all.deb) ...
Unpacking replacement evolution-data-server-common ...
Preparing to replace libedataserverui1.2-8 2.28.3.1-0ubuntu2 (using .../libedataserverui1.2-8_2.28.3.1-0ubuntu3_i386.deb) ...
Unpacking replacement libedataserverui1.2-8 ...
Preparing to replace libexchange-storage1.2-3 2.28.3.1-0ubuntu2 (using .../libexchange-storage1.2-3_2.28.3.1-0ubuntu3_i386.deb) ...
Unpacking replacement libexchange-storage1.2-3 ...
Preparing to replace evolution 2.28.3-0ubuntu9 (using .../evolution_2.28.3-0ubuntu10_i386.deb) ...
Unpacking replacement evolution ...
Preparing to replace evolution-common 2.28.3-0ubuntu9 (using .../evolution-common_2.28.3-0ubuntu10_all.deb) ...
Unpacking replacement evolution-common ...
Preparing to replace evolution-plugins 2.28.3-0ubuntu9 (using .../evolution-plugins_2.28.3-0ubuntu10_i386.deb) ...
Unpacking replacement evolution-plugins ...
Preparing to replace gstreamer0.10-plugins-good 0.10.21-1ubuntu2 (using .../gstreamer0.10-plugins-good_0.10.21-1ubuntu3_i386.deb) ...
Unpacking replacement gstreamer0.10-plugins-good ...
Preparing to replace gstreamer0.10-pulseaudio 0.10.21-1ubuntu2 (using .../gstreamer0.10-pulseaudio_0.10.21-1ubuntu3_i386.deb) ...
Unpacking replacement gstreamer0.10-pulseaudio ...
Preparing to replace libido-0.1-0 0.1.5-0ubuntu1 (using .../libido-0.1-0_0.1.6-0ubuntu1_i386.deb) ...
Unpacking replacement libido-0.1-0 ...
Preparing to replace libsdl1.2debian 1.2.14-4ubuntu1 (using .../libsdl1.2debian_1.2.14-4ubuntu1.1_i386.deb) ...
Unpacking replacement libsdl1.2debian ...
Preparing to replace libsdl1.2debian-pulseaudio 1.2.14-4ubuntu1 (using .../libsdl1.2debian-pulseaudio_1.2.14-4ubuntu1.1_i386.deb) ...
Unpacking replacement libsdl1.2debian-pulseaudio ...
Preparing to replace nvidia-current-modaliases 195.36.15-0ubuntu3 (using .../nvidia-current-modaliases_195.36.24-0ubuntu1~10.04_i386.deb) ...
Unpacking replacement nvidia-current-modaliases ...
Preparing to replace nvidia-185-modaliases 195.36.15-0ubuntu3 (using .../nvidia-185-modaliases_195.36.24-0ubuntu1~10.04_i386.deb) ...
Unpacking replacement nvidia-185-modaliases ...
Preparing to replace software-center 2.0.4 (using .../software-center_2.0.5_all.deb) ...
Unpacking replacement software-center ...
Preparing to replace telepathy-butterfly 0.5.9-0ubuntu1 (using .../telepathy-butterfly_0.5.11-0ubuntu1_all.deb) ...
Unpacking replacement telepathy-butterfly ...
Preparing to replace udisks 1.0.1-1build1 (using .../udisks_1.0.1-1ubuntu1_i386.deb) ...
Unpacking replacement udisks ...
Preparing to replace xserver-common 2:1.7.6-2ubuntu7 (using .../xserver-common_2%3a1.7.6-2ubuntu7.1_all.deb) ...
Unpacking replacement xserver-common ...
Preparing to replace xserver-xorg-core 2:1.7.6-2ubuntu7 (using .../xserver-xorg-core_2%3a1.7.6-2ubuntu7.1_i386.deb) ...
Unpacking replacement xserver-xorg-core ...
Preparing to replace fglrx-modaliases 2:8.723.1-0ubuntu3 (using .../fglrx-modaliases_2%3a8.723.1-0ubuntu4_i386.deb) ...
Unpacking replacement fglrx-modaliases ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up libaudio2 (1.9.2-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libaudio2 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmpg123-0 (1.12.1-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmpg123-0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libopenal1 (1:1.12.854-0ubuntu1~lucid1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libopenal1 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of wine1.2:
 wine1.2 depends on libaudio2; however:
  Package libaudio2 is not configured yet.
 wine1.2 depends on libmpg123-0 (>= 1.6.2); however:
  Package libmpg123-0 is not configured yet.
 wine1.2 depends on libopenal1; however:
  Package libopenal1 is not configured yet.
dpkg: error processing wine1.2 (--configure):
 dependency problems - leaving unconfigured
Setting up libkrb5support0 (1.8.1+dfsg-2ubuntu0.1) ...
No apport report written because MaxReports is reached already

Setting up libk5crypto3 (1.8.1+dfsg-2ubuntu0.1) ...

Setting up libkrb5-3 (1.8.1+dfsg-2ubuntu0.1) ...

Setting up libgssapi-krb5-2 (1.8.1+dfsg-2ubuntu0.1) ...

Setting up libedataserver1.2-11 (2.28.3.1-0ubuntu3) ...

Setting up libcamel1.2-14 (2.28.3.1-0ubuntu3) ...

Setting up libebackend1.2-0 (2.28.3.1-0ubuntu3) ...

Setting up libebook1.2-9 (2.28.3.1-0ubuntu3) ...

Setting up libecal1.2-7 (2.28.3.1-0ubuntu3) ...

Setting up libedata-book1.2-2 (2.28.3.1-0ubuntu3) ...

Setting up libedata-cal1.2-6 (2.28.3.1-0ubuntu3) ...

Setting up libegroupwise1.2-13 (2.28.3.1-0ubuntu3) ...

Setting up libgdata1.2-1 (2.28.3.1-0ubuntu3) ...

Setting up libgdata-google1.2-1 (2.28.3.1-0ubuntu3) ...

Setting up evolution-data-server-common (2.28.3.1-0ubuntu3) ...
Setting up evolution-data-server (2.28.3.1-0ubuntu3) ...
Setting up libedataserverui1.2-8 (2.28.3.1-0ubuntu3) ...

Setting up libexchange-storage1.2-3 (2.28.3.1-0ubuntu3) ...

Setting up evolution-common (2.28.3-0ubuntu10) ...
Setting up evolution (2.28.3-0ubuntu10) ...

Setting up evolution-plugins (2.28.3-0ubuntu10) ...
Setting up gstreamer0.10-plugins-good (0.10.21-1ubuntu3) ...

Setting up gstreamer0.10-pulseaudio (0.10.21-1ubuntu3) ...
Setting up libido-0.1-0 (0.1.6-0ubuntu1) ...

Setting up libsdl1.2debian-pulseaudio (1.2.14-4ubuntu1.1) ...

Setting up libsdl1.2debian (1.2.14-4ubuntu1.1) ...
Setting up nvidia-current-modaliases (195.36.24-0ubuntu1~10.04) ...
Setting up nvidia-185-modaliases (195.36.24-0ubuntu1~10.04) ...
Setting up software-center (2.0.5) ...

Setting up telepathy-butterfly (0.5.11-0ubuntu1) ...

Setting up udisks (1.0.1-1ubuntu1) ...

Setting up xserver-common (2:1.7.6-2ubuntu7.1) ...
Setting up xserver-xorg-core (2:1.7.6-2ubuntu7.1) ...

Setting up fglrx-modaliases (2:8.723.1-0ubuntu4) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Processing triggers for python-central ...
Errors were encountered while processing:
 libaudio2
 libmpg123-0
 libopenal1
 wine1.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
joris@joris-desktop:~$ sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  watershed libreadline5
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  alsa-oss
0 upgraded, 1 newly installed, 6 reinstalled, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 837kB/1,921kB of archives.
After this operation, 156kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://nl.archive.ubuntu.com/ubuntu/ lucid/main alsa-base 1.0.22.1+dfsg-0ubuntu3 [273kB]
Get:2 http://nl.archive.ubuntu.com/ubuntu/ lucid/universe alsa-oss 1.0.17-3 [32.1kB]
Get:3 http://nl.archive.ubuntu.com/ubuntu/ lucid/main gstreamer0.10-alsa 0.10.28-1 [35.9kB]
Get:4 http://nl.archive.ubuntu.com/ubuntu/ lucid/main libasound2 1.0.22-0ubuntu7 [394kB]
Get:5 http://nl.archive.ubuntu.com/ubuntu/ lucid/main libasound2-plugins 1.0.22-0ubuntu6 [68.6kB]
Get:6 http://nl.archive.ubuntu.com/ubuntu/ lucid/main linux-sound-base 1.0.22.1+dfsg-0ubuntu3 [33.7kB]
Fetched 837kB in 5s (156kB/s)        
Preconfiguring packages ...
(Reading database ... 149618 files and directories currently installed.)
Preparing to replace alsa-base 1.0.22.1+dfsg-0ubuntu3 (using .../alsa-base_1.0.22.1+dfsg-0ubuntu3_all.deb) ...
Unpacking replacement alsa-base ...
Selecting previously deselected package alsa-oss.
Unpacking alsa-oss (from .../alsa-oss_1.0.17-3_i386.deb) ...
Preparing to replace alsa-utils 1.0.22-0ubuntu5 (using .../alsa-utils_1.0.22-0ubuntu5_i386.deb) ...
Unpacking replacement alsa-utils ...
Preparing to replace gstreamer0.10-alsa 0.10.28-1 (using .../gstreamer0.10-alsa_0.10.28-1_i386.deb) ...
Unpacking replacement gstreamer0.10-alsa ...
Preparing to replace libasound2 1.0.22-0ubuntu7 (using .../libasound2_1.0.22-0ubuntu7_i386.deb) ...
Unpacking replacement libasound2 ...
Preparing to replace libasound2-plugins 1.0.22-0ubuntu6 (using .../libasound2-plugins_1.0.22-0ubuntu6_i386.deb) ...
Unpacking replacement libasound2-plugins ...
Preparing to replace linux-sound-base 1.0.22.1+dfsg-0ubuntu3 (using .../linux-sound-base_1.0.22.1+dfsg-0ubuntu3_all.deb) ...
Unpacking replacement linux-sound-base ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libaudio2 (1.9.2-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libaudio2 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmpg123-0 (1.12.1-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmpg123-0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libopenal1 (1:1.12.854-0ubuntu1~lucid1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libopenal1 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of wine1.2:
 wine1.2 depends on libaudio2; however:
  Package libaudio2 is not configured yet.
 wine1.2 depends on libmpg123-0 (>= 1.6.2); however:
  Package libmpg123-0 is not configured yet.
 wine1.2 depends on libopenal1; however:
  Package libopenal1 is not configured yet.
dpkg: error processing wine1.2 (--configure):
 dependency problems - leaving unconfigured
Setting up libasound2 (1.0.22-0ubuntu7) ...
No apport report written because MaxReports is reached already

Setting up libasound2-plugins (1.0.22-0ubuntu6) ...
Setting up linux-sound-base (1.0.22.1+dfsg-0ubuntu3) ...

Setting up alsa-base (1.0.22.1+dfsg-0ubuntu3) ...

Setting up alsa-oss (1.0.17-3) ...

Setting up alsa-utils (1.0.22-0ubuntu5) ...

Setting up gstreamer0.10-alsa (0.10.28-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libaudio2
 libmpg123-0
 libopenal1
 wine1.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
joris@joris-desktop:~$ 

```

---

### Post by lidex on 2010-06-17
OK. How about this output now:
```
aplay -l
```

---

### Post by joggleh on 2010-06-18
> **lidex said:**
> OK. How about this output now:
```
aplay -l
```

No longer needed. It works! Thank you SO much. 

But here you go:

```
card 0: M5455 [ALi M5455], device 0: Intel ICH [ALi M5455]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: M5455 [ALi M5455], device 2: Intel ICH - IEC958 [ALi M5455 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by lidex on 2010-06-18
Sweet. If you would please mark the thread as solved using 'Thread Tools' up top.

---

### Post by joggleh on 2010-06-19
> **lidex said:**
> Sweet. If you would please mark the thread as solved using 'Thread Tools' up top.

I would love to but... After a reboot it stopped working again.

Aplay -l gives me:

```
aplay: device_list:223: no soundcards found...

```

---

### Post by lidex on 2010-06-19
Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by joggleh on 2010-06-20
> **lidex said:**
> Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```Enter your user password when prompted. Provide a link for the output or post it here using code tags.

[http://www.alsa-project.org/db/?f=94e6a284df75d6e2f401abf19bb34c166c7942d4](http://www.alsa-project.org/db/?f=94e6a284df75d6e2f401abf19bb34c166c7942d4)

```
!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)

```

:confused:

---

### Post by joggleh on 2010-06-20
> **joggleh said:**
> [http://www.alsa-project.org/db/?f=94e6a284df75d6e2f401abf19bb34c166c7942d4](http://www.alsa-project.org/db/?f=94e6a284df75d6e2f401abf19bb34c166c7942d4)

```
!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:04.0 Multimedia audio controller: ALi Corporation M5455 PCI AC-Link Controller Audio Device (rev 20)

```:confused:

Nevermind. Editing my alsa base file like this: [http://ubuntuforums.org/archive/index.php/t-317061.html](http://ubuntuforums.org/archive/index.php/t-317061.html) helped me out. Thanks a lot for your help though;).

I will mark the thread as solved.

---

### Post by j800r on 2010-07-06
i know this is a solved thread, and my problem is not exactly the same, and moderators can feel free to move this post if it's in the wrong place.

I have a problem with my soundmax 5.1 card (which came with my Striker II Extreme motherboard.) I set it to a 5.1 analogue output with stereo input profile, and the sound worked fine, except there was no signal being sent to the subwoofer. my other speakers are only small satellite speakers and can't produce bass frequencies. I have seen nothing to control crossover in the sound settings, in my Windows 7 setup I have the crossover set at 130hz and it works brilliantly.

Can someone please help with this matter as it's the only thing keeping me from using Ubuntu full time on this system (btw, i have used the same speakers in a different PC with ubuntu as it's prime OS with a stereo setup and it worked fine. It's just when set up for 5.1 that the Subwoofer doesn't kick in (during music playback etc)

---

### Post by mitt_matt on 2010-08-31
Hi, I'm new in here. Hope someone can help me, for my problem is the same.
I installed Ubuntu 10.04 and the only thing that doesn't work is the sound. I've an Olidata laptop and SoundMAX integrated Digital Audio sound board. 
I've been looking around for some solutions and it seems that the problem is common.
If you have suggestions... I'm not an expert in linux.
Last thing, the system sees the sound board and the alsamixer seems to work normally but i have no sound.
Thank you

---

### Post by lidex on 2010-08-31
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by mitt_matt on 2010-09-02
HI again,
I've been looking around and found one with same laptop who resolved.
Just for knowledge, it was that in the alsamixer the External volume was on and it had to be turned off.

Now my problem is that when I reboot it begins again with External volume ON, how can I do to save settings in alsamixer?
Thanks

---

### Post by lidex on 2010-09-02
> **mitt_matt said:**
> HI again,
I've been looking around and found one with same laptop who resolved.
Just for knowledge, it was that in the alsamixer the External volume was on and it had to be turned off.

Now my problem is that when I reboot it begins again with External volume ON, how can I do to save settings in alsamixer?
Thanks

Do you mean EAPD - external amplifier?

Set your mixer up as needed and run this command:
```
sudo alsactl store 0
```

---

### Post by mitt_matt on 2010-09-04
I tried but the response is
Home folder /home/donega is not ours.
What does this means?

---

