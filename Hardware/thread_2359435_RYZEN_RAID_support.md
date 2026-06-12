---
title: "RYZEN RAID support"
date: 2017-04-24
forum: Hardware
---

### Post by sarwarr87 on 2017-04-24
Hi,

I have a Zen 1600 CPU running on MSI B350M Mortar 1.2 BIOS.

I have three disks: 2x SSD and 1 HDD

Ussual configeration that I do:
RAID0 => 2xSSD
unRAIDED => HDD

the RAID0 is used as the windows boot drive. while the HDD's partition contains the Ubuntu along with other data partitions. All SATA ports are connected to the RAID controller. The AMD RAID controller that comes with the MB (v8) requires the unRAIDED partition to be connected to a RAID-VOLUME, their version of single disk usage.

I was trying to install Ubuntu this weekend when i realized that the disks are not detected my the LiveUSB. fdisk -l comes up with only the USB partition, and only \dev\sda is listed which is the USB again. I tried Ubuntu 16.4.1 16.4.2 and 17.4, all have the same problem. I downloaded the RAID driver from the AMD website for Linux_amd64 and installed it from busybox on 16.4.1 (the newer versions are not supported yet and will not install complaining that 4.4 kernel is needed), but it did not help as the drives were still undetected.

In the end i came up with a dirty fix of:
1. install RAID0 and install windows in it.
2. wipe MRB on HDD
3. switch to ACHI in BIOS and install Ubuntu on HDD.
4. switch to RAID to restore HDD.

now to switch between Ubuntu and windows, i have to go to bios and activate/deactivate RAID. I still have access to the HDD from both OS, but there is access to RAID0 SSDs from ubuntu.

I was wondering if there was a better solution out there that can solve this problem. If you need more info, please do let me know.

Cheers

---

### Post by TheFu on 2017-04-24
Welcome to the forums.

You have some options, as I see it.

a) Don't use fakeRAID.  It has all the slowness of SW-RAID, but all the HW dependencies of real HW-RAID without any of the fantastic performance.

b) Run Windows in a VM under Ubuntu.  Then you can use KVM, Xen, VirtualBox, or a few other hypervisors which have lots of great options. You can use Linux SW-RAID, which is extremely flexible.  I've moved RAID disks between multiple, different motherboards, JBOD controllers, and vastly different CPUs.  Of course, your Windows license will need to allow this.  With KVM, I've never had any stability issues.  I know people who run Xen and others who run virtualbox happily as well, though both of those had different issues for my systems. 

c) Run Ubuntu in a VM under Windows.  You are limited to Windows-only hypervisors.  You can use FakeRAID.  You'll have to deal with a slightly less stable hostOS, but Windows since Win7 really has been very stable, IME. I routinely got over a month between reboots.

Any modern CPU better than a Core2Duo can easily run virtual machines.

Backups are 1000x more important than RAID. There are 3 reasons for RAID and 1000 reasons for backups.  When RAID fails, sometimes, usually, restoring from a backup is the solution. Just search these forums for all the issues with RAID.  Just sayin'.

---

