---
title: "External HDD gone AWOL"
date: 2010-04-27
forum: Hardware
---

### Post by serpentsix on 2010-04-27
Hi
I have been using a 20Gb HDD via usb connection from an old windows machine for about a year[i keep client data on it]. It was only recognized in /media if i turned it on during boot up[not a problem].
But two weeks ago it didn't appear? so looked in "sudo fdisk -l" :-

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd2bed2be

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2325    18675531   83  Linux
/dev/sda2            2326        2432      859477+   5  Extended
/dev/sda5            2326        2432      859446   82  Linux swap / Solaris

no HDD was visible ?? but when I run lsusb :-

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 04f3:0230 Elan Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 13fd:0550 Initio Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Its visible - device 009

I coundnt understand why its not in the mount? so i tried to see if a windows machine would see it= proving drive and cables and when plugged in, its seen in "disk management" as a drive with unknown system, which i expected as i set it up as ext3...
I have 5 other usb ports on the Intrepid Ibex machine and the same result was found when plugged into any of them, but i knew they are working as I have a mouse which works in all ports.

has anyone any idea how i can get this drive recognized again without wiping the data on it and reformatting etc?

any advice greatly appreciated....

S

---

### Post by serpentsix on 2010-04-28
bump

anyone?

---

