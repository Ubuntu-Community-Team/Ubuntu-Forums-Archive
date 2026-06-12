---
title: "usb drive prevents ubuntu from seeing NTFS and DVD drive"
date: 2011-03-09
forum: Hardware
---

### Post by silviucc on 2011-03-09
Hello,

I'm posting this under HW as I'm not quite sure where to put it.

I dual boot my system with Windows 7(64bit) Home Premium and Ubuntu 10.04 32bit (pae kernel). Under windows I used an "expendable" 4GB USB flash drive for Readyboost. When I booted to Ubuntu the OS would not see my DVD drive and when going for 
System -> Administration -> Disk Utility this program would not start. Also, inserting USB drives and DVDs would not make them show up on the desktop. Doing a dmesg | tail would reveal that the USB drive being inserted or removed would trigger events accordingly. 

So I wondered what I had modified between my last session with Ubuntu that would trigger something like this. Well my "readyboost" flash drive is inserted but that could not be the cause, could it? So I reomved it from the USB port and rebooted.

Yep, there they are, my NTFS oartitions ready to be mounted, my DVD drive, disk uitlity starts works.


I have noticed this with Ubuntu 10.10 64bit as well. What the heck happened ? Anyone else had something like this happen to them ?

System specs:

CPU: Intel E7400| MB: GA-EP31-DS3L | RAM: 4GB DDR2 Kingston HyperX | HDDs 1x640 GB + 1x250GB + 1x80GB |
Video: Gigabyte GeForce GTX 260 core 216 | PSU Cooler Master GX 750W

the USB drive in question is formatted with FAT16 - which is weird since I knew FAT16 volumes could have only 2GB *sigh*

---

