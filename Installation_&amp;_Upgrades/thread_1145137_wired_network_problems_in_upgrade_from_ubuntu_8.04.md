---
title: "wired network problems in upgrade from ubuntu 8.04 to 8.10"
date: 2009-05-01
forum: Installation &amp; Upgrades
---

### Post by y10linux on 2009-05-01
Hi! 

After reading these forums for quite a long time I finally registered, this is my first post.

I upgraded recently from Ubuntu 8.04 to 8.10 and my wired network stopped working. Here are some details:

- The wired network did work before (I actually downloaded the files necessary for the upgrade via a wired network).

- The wireless controler keeps on working and I can connect to the internet via wireless but not via wired network (I have tired two different wired networks so far).

I am using Network Manager and the networking is enabled (I have also tried to disable it and enable it again and it didn't work). When I click in the wired network icon, it opens a small dialog that says that the **wired network is unmanaged** (and currently displays the name of the wireless network I am connected to.

1) I have tried several things without success and believe that the problem is here:

:~$ lspci -nnm|grep 14e4
03:00.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "BCM4401-B0 100Base-TX [170c]" -r02 "Dell [1028]" "Device [01f2]"

I think a "Network Controller" is missing, but do not know how to install it. 

2) I thought there might be firmware problems, but this page seems to indicate that my ethernet card (BCM4401-B0 100Base-TX) does not need them:
[http://www.fsf.org/resources/hw/net/wired-ethernet](http://www.fsf.org/resources/hw/net/wired-ethernet)

3)  lshw -C network

returns:

WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:8c:98:e8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.3 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:be:b8:ed
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=84.88.154.117 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: d2:e0:bd:88:8a:c4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


which seems to indicate that the device is off, there is no way to physically turn it on (at least not that I know about). I never did turn it on in Ubuntu 7.10 or 8.04 where the wired network worked just fine.

Well thanks for reading all these and I hope I happened to provide some useful information.

---

### Post by zvacet on 2009-05-01
Similar thing here,but I have just one connection and even network manager is telling me that device is unmanaged I have connection.Well,that is not what are you asking.Try to put in /etc/network/interfaces this lines

> auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

---

### Post by y10linux on 2009-05-02
> **zvacet said:**
> Similar thing here,but I have just one connection and even network manager is telling me that device is unmanaged I have connection.Well,that is not what are you asking.Try to put in /etc/network/interfaces this lines

The file you mention contains:

auto lo
iface lo inet loopback


iface eth0 inet static
address 84.88.154.117
netmask 255.255.254.0
gateway 84.88.154.1

auto eth0

Should I add the line:

iface eth0 inet dhcp 			 		

at the end of the file?

---

### Post by y10linux on 2009-05-03
> **zvacet said:**
> Similar thing here,but I have just one connection and even network manager is telling me that device is unmanaged I have connection.Well,that is not what are you asking.Try to put in /etc/network/interfaces this lines

Well, tried that and it does not seem to work...

Thanks for your help anyway, I'm going to keep trying to solve this...

---

### Post by deeppow on 2009-05-04
Same problem here with new install of 8.10   Also tried 9.04, same problem.  

Instructions in either version of help are of no use, plus must be written for older versions.  

I had 8.04 working awhile back with no problems.

---

### Post by deeppow on 2009-05-04
If you have a Marvell Yukon connector, try this link [http://ubuntuforums.org/showthread.php?t=781022](http://ubuntuforums.org/showthread.php?t=781022)

---

### Post by y10linux on 2009-05-05
In this thread [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/357509](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/357509) and the references therein you can find some more information.

I finally got to "solve" the problem (in 9.04) by erasing all the interfaces (that seemed to be ignored anyway) in /etc/network/interfaces and leave this files with just two lines:

auto lo
iface lo inet loopback

THEN I configured my wired network with network manager and got it working at work (where I have a fixed internet address). I still haven't managed to get it working at home, but I have not been able to dedicate much time to it yet.

---

### Post by stretch427 on 2009-05-05
If it only works at your work, and not at home it could also be a router problem, or should I say an oddly configured setting. 

I know with my router I sometimes have to set to allow certain computers and stuff. Just a thought.  Maybe try resetting your home router or modem, whichever you have. 

Cheers!

---

