---
title: "DVB-T USB Dongle"
date: 2011-02-02
forum: Hardware
---

### Post by The Browncoat Cat on 2011-02-02
I have bought a BlazeDTV 6.0 DVB-T USB Dongle.  It comes with Windows installation software, and works fine on the XP Partition on my netbook, but I want it to run under Ubuntu (10.10 Maverick) as well.  

When I plug it in the command "lsusb" produces the following result:
```
 windsor@windsor-netbook:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick
Bus 001 Device 002: ID 0ac8:c33f Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
windsor@windsor-netbook:~$ 
```

I have downloaded and installed the retricted firmware for DVB cards via "System > Administration > Additional Drivers" and MeTV to watch and record the DVB-T broadcast with. However, the blue LED on the dongle that shows that it is receiving a signal and feeding it to the computer does not light up, and when I try to set the channels with MeTV, it tells me that "No DVB Device is Present".  

Am I missing something, is there another command I need to enter via the terminal or a piece of software that I still need to download.  Any assistance gratefully accepted.

---

### Post by The Browncoat Cat on 2011-02-06
bump!):P

---

### Post by TopEnder on 2011-02-07
> **The Browncoat Cat said:**
> I have bought a BlazeDTV 6.0 DVB-T USB Dongle.  It comes with Windows installation software, and works fine on the XP Partition on my netbook, but I want it to run under Ubuntu (10.10 Maverick) as well.  

When I plug it in the command "lsusb" produces the following result:
```
 windsor@windsor-netbook:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick
Bus 001 Device 002: ID 0ac8:c33f Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
windsor@windsor-netbook:~$ 
```

I have downloaded and installed the retricted firmware for DVB cards via "System > Administration > Additional Drivers" and MeTV to watch and record the DVB-T broadcast with. However, the blue LED on the dongle that shows that it is receiving a signal and feeding it to the computer does not light up, and when I try to set the channels with MeTV, it tells me that "No DVB Device is Present".  

Am I missing something, is there another command I need to enter via the terminal or a piece of software that I still need to download.  Any assistance gratefully accepted.

The Browncoat,  I have the same USB dongle (ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick) and have been using it in 9.04, 9.10 ,10.04 & 10.10.  The only problem I have had was with that thing they call an aerial, run my stick on the main house antenna, no additional drivers or software required.  I believe the Windows installation picks up better than the Ubuntu MeTV installation until it's tweaked but is still does not match the . VLC (VideoLan) Media Player for speed I find it's a better option for me. TopEnder

---

### Post by markthekdeguy on 2011-02-08
i have had probs with me-tv for years.
i use KDE  so i use Kaffeine .. 
in fact i use an old version of Kaffeine.

if you get no luck with the new version of Kaffeine, heres a nice old version i use .. its the bottom one
[kaffeine_0.8.8-0ubuntu1~jaunty~ppa1_i386.deb]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa/+buildjob/1118537/+files/kaffeine_0.8.8-0ubuntu1%7Ejaunty%7Eppa1_i386.deb")         (3.2 MiB)       

on this page.

[https://launchpad.net/~nvidia-vdpau/+archive/ppa/+buildjob/1118537]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa/+buildjob/1118537")

but it will want to install some KDE stuff. but i think its the best DVB-T
for linux yet. hope you get it working ok.

---

