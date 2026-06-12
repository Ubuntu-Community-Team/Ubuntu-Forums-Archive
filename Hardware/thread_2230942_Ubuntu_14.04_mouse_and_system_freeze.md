---
title: "Ubuntu 14.04 mouse and system freeze"
date: 2014-06-22
forum: Hardware
---

### Post by Micski on 2014-06-22
I am one of those thousands of users, who experiences frequent freezes and system locks with Ubuntu over the years. 14.04 is no different:

I did a fresh install of Ubuntu 14.04 LTS on a newer standard Intel hardware computer and on a brand new harddisk. Installed all updates and kernel 3.13.0-29-generic. Default settings for desktop environment.

Motherboard is Gigabyte Technology Co. HA65M-D2H-B3 with up to date Award Software International F12 BIOS, 4x Intel(R) Core(TM) i5-2500 CPU @ 3.30GHz processors, 8 MB RAM and NVIDIA Corporation GT218 [GeForce 210] (rev a2) graphics adapter. Using the recommended and tested NVidia binary 331.38 proprietary driver.

The same machine runs FreeBSD, Gnome and Compiz 3D desktop environment perfectly. Even Windows.

However, once again Ubuntu has managed to release a "stable" system, that not only freezes the mouse within short time of use or no use, but also manages to completely freeze the system in a manner, that leaves nothing left but a hardware reset or power-off. No terminal access. No SSH access. No ping reply. Nothing.

This is not only a problem in 14.04. It is/was also a problem in 13.10, 13.04, 12.10, 12.04, 11.10, 11.04, 10.10 and 10.04. Also on different hardware. 

It is extremely rare, that a system completely locks up and freezes. Even for Windows. Except for Ubuntu. The developers keep telling us, that Ubuntu is perfect - and we have to update BIOS, drivers and even use new disks. Extensive measures has to be done. A few are able to do this - and to no succes. Thanks, guys.

There is no doubt, that this issue is close to unresolvable, so I am expecting no quick workable solutions here. However, I am open to serious expert comments about this subject. I am very curious as to why this system is not 0.14.04 as it should be - and so different from other real stable systems.

---

### Post by -Marco on 2014-06-22
Do you have a **UEFI BIOS** and you have to install the distro following a special procedure. 
You also have a VGA that do worst than integrated GPU intel (in that case you've a HD 3000/3100). 
The drivers of the old nVIDIA VGA are horrible, even I, who had the G100 had put the open-source drivers for Ubuntu. 


Try to reinstall everything from scratch using GParted and creating the mapping GPT with adjoining FAT32 partition to boot and then .. **avoid installing proprietary drivers nVIDIA**

---

