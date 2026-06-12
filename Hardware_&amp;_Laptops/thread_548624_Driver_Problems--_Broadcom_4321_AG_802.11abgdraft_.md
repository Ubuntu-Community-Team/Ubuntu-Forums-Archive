---
title: "Driver Problems-- Broadcom 4321 AG 802.11a/b/g/draft n wi-fi card"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by 1337_ubunutu_teen on 2007-09-11
I have an HP Compaq 6715b that is currently running Feisty.   I cannot get my wireless card to work.  Does anyone know how I can do so??

---

### Post by Amivit on 2007-09-27
I would love to know too.

---

### Post by mikedep333 on 2007-09-27
I just tried setting up ndiswrapper on gutsy x86 beta with both a broadcom driver from december 06 and one from july07 (4.150.22.0.) Both times it was bcmwl6 instead of bcmwl5 like in instructions for their 802.11g cards. Ndiswrapper loads the driver, and the kernel module for ndiswrapper is loaded, but not device identifier (like eth1 or wlan0) shows up. It is therefore unusable.

EDIT: same problem with the june 06 or so dell bcmwl5 driver mentioned here:
[http://ubuntuforums.org/showthread.php?t=263721](http://ubuntuforums.org/showthread.php?t=263721)

---

### Post by polydiet on 2007-10-23
I got exactly the same!
After installing the bcmwl6 driver, no interfase is created.

---

### Post by pdxpete on 2007-11-11
HP dv6000 with broadcom 4321AG.  No Wireless on Gutsy fresh install.  Please help.:confused:

---

### Post by gabr10 on 2007-12-22
Same thing here.. HP Pavilion dv6646us, would love to get an answer I'm freaking out

---

### Post by gfd_2 on 2007-12-22
same problem... HP dv6633us ... loading with ndiswrapper and the network shows as DISABLED?!?!
:
dcb@dcb-laptop:~$ sudo lshw -C network 
  *-network DISABLED      
       description: Wireless interface 
       product: BCM94311MCG wlan mini-PCI 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: wlan0 
       version: 02 
       serial: 00:1a:73:d7:d6:fe 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.45+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

---

### Post by gabr10 on 2007-12-22
Got it working!!! I used this:
[http://ubuntuforums.org/showthread.php?t=575750&highlight=broadcom+4321](http://ubuntuforums.org/showthread.php?t=575750&highlight=broadcom+4321)

Only the part of the wireless card setup on the first post, and with the driver that he provides. It is working perfectly since.

:):):):):):):):)

---

### Post by Er1ck on 2008-03-30
[http://ubuntuforums.org/showthread.php?t=336654&page=2](http://ubuntuforums.org/showthread.php?t=336654&page=2)

I have the HP DV6646US laptop and after reading through the thread (link is posted above) I was able to get my wireless fully working and functioning with Ubuntu Fiesty Fawn.

-Erick

---

### Post by bigal947 on 2008-05-21
Finally it all works!!

I have been lurking on linux for the last 5 years attempting to migrate away from MS Windows. I have been on unix/linux workstations for at least 20 years and have come to the conclusion that the Linux community matra was "if it don't hurt it isn't worth it". In particular I haven't been able to get my wireless working. Well I just hear that Ubuntu 8.04 is "seamless" so off I went away from the "dark side" again. Ubuntu loaded in Windows just fine, but as always the wireless didn't connect. So here I go again.
My windows device manager indicated a Broadcom 4321AG so off to the postings and all that ndiswrapper stuff. No luck, some flashes of operation but not stable at all. A day latter I somehow ran into the 8.04 documentation (if all fails, read the manual) and I find this Using the section on  [Windows and Drivers]("https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html") and it worked!!! (I used the bcmwl5 .sys and .inf). I should of gone here first.
As far as I am concerned Linux is here!!:smile:

---

### Post by Cataleya on 2008-05-21
Wow!  I am having the same problems with an HP, AMD 64 trying to get my Broadcom 4318 installed.

Can you walk a newbie through the steps?  To locate and install? 

Sure would appreciate.

---

### Post by bigal947 on 2008-05-22
First you have to get hold of the drivers for your wireless. It looks as if you have the same HP configuration that I have (tx1220us). I used bcmwl5.inf and .sys You will have to get the drivers you need. I found them at Dell's site. HP has bcmw6, I am not sure this one works. 

Next go to the following link to get the gtk-ndis
[Using Windows Wireless Drivers]("https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html")

Wish you the best.

Al

---

