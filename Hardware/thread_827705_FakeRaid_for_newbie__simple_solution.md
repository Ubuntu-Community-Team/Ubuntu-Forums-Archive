---
title: "FakeRaid for newbie : simple solution"
date: 2008-06-13
forum: Hardware
---

### Post by formol on 2008-06-13
Hello,

This is a simple solution I figure out to how to set up a Raid1 configuration without using the long method available here [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto").

I did Raid1, two identical hard disk, but I guest this method would work for Raid0 too or other raid configuration offered by your motherboard.

first thing to know.  most of the motherboard have so-call FakeRaid, who are small implementation on motherboard to make software raid more easy. hardware raid are very rare and expensive.

so, my simple raid1 solution is:

- burn and run the ubuntu-server 

- when you get to the partition windows, choose manual

the configuration for Raid1 is   

RAID1 device 1 = X Gb = swap
RAID1 device 2 = Y GB = /         etx3
RAID1 devince 3 = Z Gb = ext3,  rest of the disk, you can mount it where you want

SCSI1 (0,0,0) (sda) 
1 primary X Gb boot raid aray
2 primary Y Gb      raid aray
3 primary Z Gb      raid aray


SCSI1 (0,1,0) (sdb) 
1 primary X Gb      raid aray
2 primary Y Gb      raid aray
3 primary Z Gb      raid aray

to do that, choose split your both disk into identical partition and choose raid for each (instead of etx3).  then set up the raid aray with euqal size.  one of the raid disk of the / must be boot.  don't forget when it's time to boot to choose raid in the boot order in the bios.  also in the bios, I don't know for all FakeRaid configuration, but for mine, nvraid, it needed to be disable, Ubuntu take it totally in charge. 

and finish the installation of ubuntu server. 

when you boot and get in the command line of the server, 

> sudo apt-get update
> sudo apt-get update

and, enter

> sudo apt-get install ubuntu-desktop

it will bring you the gnome graphical interface, kubuntu and others are also available.

reboot.  you are now in a ubuntu-server computer with graphical interface.

install the generic kernel.

the last kernel is actually 2.6.24-18-generic [http://packages.ubuntu.com/hardy/linux-ubuntu-modules-2.6.24-18-generic]("http://packages.ubuntu.com/hardy/linux-ubuntu-modules-2.6.24-18-generic")

install it .deb installer works for me. 

then

> sudo apt-get install linux-headers-`uname -r` build-essential 

and now, you are reader to install your video, and sound if no sound, drivers.

---

