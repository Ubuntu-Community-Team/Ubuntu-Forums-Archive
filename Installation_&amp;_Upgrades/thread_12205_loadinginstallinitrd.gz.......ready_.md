---
title: "loading/install/initrd.gz.......ready_???"
date: 2005-01-22
forum: Installation &amp; Upgrades
---

### Post by alsilverbert on 2005-01-22
I tried to install a Warty Warthog Release on a CD of the german magazine "linux-user".
After the welcome-screen there followed three lines:
loading/install/vmlinuz.......
loading/install/initrd.gz...........
Ready
_

That´s all!
After that I downloaded an "iso", burnt it and tried to install:
the same result!
My PC: 500MHz;  192MB RAM; 13GB HHD

I read that acpi should be switched off in BIOS , there is no acpi, but any power-management is switched off. 
....read that apm should be entered in /etc/modules, but what for when linux isn´t installed yet.....

................any idea ?

---

### Post by shmonkey on 2005-01-23
Initially sounded like a corrupt iso image but as you have downloaded an iso as well, I guess we can rule this out (do an MD5 checksum test to make sure though).

Seems that you are having problems loading the kernel image into memory. This may be something about your cdrom drive that is causing a problem. 

Maybe if you post more details about your system, someone will be able to help you more.

You could also see if you have any luck with Knoppix.

---

### Post by alsilverbert on 2005-01-23
Which system-details could be useful?

---

### Post by alsilverbert on 2005-01-23
Now I m online with Morphix-Live-CD - no problem at all...........
I still don t understand my problem with UBUNTU - installation!!!!!!!

---

### Post by shmonkey on 2005-01-23
It's possible that the Ubuntu kernel image is not setup very well to cope with your hardware. By your system specs I mean't :

processor
m/board
hdd (type)
any other details you like ....!!!

---

### Post by alsilverbert on 2005-01-27
Thanks for your interest, last days I was too busy otherwise..............

My PC
Prozessor-type:      Intel (R)  Pentium (R) II
Prozessor-speed:   500MHz
Cache-RAM:           512KB
Total-Memory          192 MB  SDRAM

Motherboard           Intel SR440BX
                                                          TM
Grafik on board       nVidia RIVA TNT         128 Bit  3D Multimedia
                                 accelerator-chip 16 MB SDRAM
Audio on Board       Creative Sound Blaster Audio PCI 64V     FS1373

BIOS                      Intel   BIOS
                              Intel E28F004S5 4Mbit Flash-Memory
                              Support for SMBIOS, APM, 
                              ACPI and Plug and Play

dev/hda            74,5GB        Samsung SV0802N                                   0    -     9732
       hda1            7,8GB        Win95 FAT 32 LBA         /Windows/C         0    -    1021
       hda2            66,7GB       extended                                              1022   -   9732
       hda5            15,6MB       F Linux native (Ext 2)     /boot               1022   -   1023
       hda6            164,7MB     F Linux swap                  swap               1024   -   1044
       hda7              66,5GB     F Linux native  (Ext2)      /                      1045   -   9732

dev/hdb              12,6GB        ST 313640A                                            0   -   1652
       hdb1            12,5GB         Win95 FAT 32   LBA                               0   -   1652

I disconnected the second HHD from master HDD and tried to install UBUNTU there, the result just as told, I also tried to install on hda. There I din´t want to complete it, but I saw it didn´t work.

---

