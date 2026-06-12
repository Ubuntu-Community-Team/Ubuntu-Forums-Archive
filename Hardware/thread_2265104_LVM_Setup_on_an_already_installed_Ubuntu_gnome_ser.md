---
title: "LVM Setup on an already installed Ubuntu gnome server"
date: 2015-02-12
forum: Hardware
---

### Post by Christopher_J._Cra on 2015-02-12
Hello everyone, I'm trying to set up an LVM on my File sharing server. The server has ubuntu 14.04 lts 64 bit running on a pentium dual core E2140 @ 1.60Z GHz with 1gb of memory (will be getting upgraded to 2 gb). The server is also running the latest version of Gnome. For drives right now I have 7 drives in the server:

Model: ATA IC35L04AVVA07-0
Size: 31.50 GB
Path: /dev/sda
File System: NTFS

Model: ATA IC35L04AVVA07-0
Size: 31.50 GB
Path: /dev/sdb
File System: NTFS

Model: ATA WDC WD400BB-60DG
Size: 37.27 GB
Path: /dev/sdc (this is the OS hard drive)
File Systems: sdc1 - ext4  sdc2 - extended sdc5 - linux-swap

Model: ATA Quantum Fireball
Size: 19.01 GB
Path: /dev/sdd
File Systems: sdd1 - extended (unallocated)

Model: ATA ST3250310AS
Size: 232.83 GB
Path: /dev/sde
File System: NTFS

Model: ATA WDC WD3200AAJS-6
Size: 298.09 GB
Path: /dev/sdf
File System: NTFS

Model: WD I HDS72 External
Size: 465.76 GB
Path: /dev/sdg
File Systems: sdg1 - extended  New Partition #1 - lvm2 pv

I have no cd roms in the tower and no usb flash drives to do a live cd boot. what I want to do is first setup the group with sdd and sdg and move the files from the other drives to it (except the os drive) then I want to add the other drives to the group making it act as a drive with a little over a TB is there any way to do this without having to do a clean install or boot from a live cd? (I really don't want to do a clean install it takes a long time to get everything running correctly) if any other info is needed please let me know and I will get it for you. Thank you for your time and help :-) Christopher J. Crandall

---

### Post by Christopher_J._Cra on 2015-02-12
I have installed lvm 2 on the os but didn't setup lvm when I installed the os

---

### Post by Christopher_J._Cra on 2015-02-12
I keep getting the error: /dev/sdg not found (or ignored by filtering)  when I use the command sudo vgcreate KC-Computers /dev/sdg1 .the same is for sdg1 and sdd

---

### Post by Christopher_J._Cra on 2015-02-12
well I'm going to do the fresh install unhooked one of the internal hard drives and hooked a dvd rom up. going to upgrade to the newest server version 14.10 64bit. maybe that will fix some of the bugs I've been having. I'll let you know how things fair out

---

