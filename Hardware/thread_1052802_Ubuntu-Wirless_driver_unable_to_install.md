---
title: "Ubuntu-Wirless driver unable to install"
date: 2009-01-28
forum: Hardware
---

### Post by dvl300 on 2009-01-28
i have a buffalo wireless n-infiniti(UCG300N) usb adaptor when i installed ubuntu and ndis wrapper and the windows driver with ndis wrapper the wireless card does not work what have i done wrong?

any suggestions?

---

### Post by teaker1s on 2009-01-28
hi fire up terminal,
```
lsusb
```
post output and I will look for some decent instructions

---

### Post by dvl300 on 2009-01-29
silverdragon@silverdragon:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 145f:011a  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 1b1c:1928  
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0411:00e8 MelCo., Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
silverdragon@silverdragon:~$ 

i have removed the wireless usb and then ran lsusb and then re-inserted the wireless usb and can confirm it is attached by the following device line-**Bus 001 Device 002: ID 0411:00e8 MelCo., Inc. **

Quick note i downloaded and installed the ubuntu 8.10 32-bit I386 version
but i have an intel core2duo so do i need to install the 64-bit version instead-just downloaded!
NOT INSTALLED YET!

---

### Post by dvl300 on 2009-01-29
solved it turns out i hadn't installed all the repository files for ndiswrapper as i have now found out by running the ubuntu linux live cd
on a friends PC with an INTERNET connection and typing Windows Wireless Drivers in Add/Remove Application and in description clicked this link [http://jak-linux.org/projects/ndisgtk/]("http://jak-linux.org/projects/ndisgtk/")
and downloaded and installed the following files in order
1.ndiswrapper-common_1.52-1ubuntu1_all.deb
2.ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb
3.and last but not least ndisgtk_0.8.4-1_i386.deb

then went to system>administration>windows wireless drivers
and clicked install new driver
wireless usb adapter was recognized install and functioning properly
then all i had to do was click on the network icon in the top right
of the screen and select my wireless network and enter the WPA KEY
and it worked as i am now posting this now!
(Note:Restart Maybe Required-In Some Cases?)
now i can use UBUNTU to its full potential!

---

