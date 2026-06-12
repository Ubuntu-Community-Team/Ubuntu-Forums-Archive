---
title: "System shuts down when mounting sata dvd drive"
date: 2008-09-14
forum: General Help
---

### Post by onnix on 2008-09-14
Greetings 

Whenever i try to insert a dvd or cd on a sata drive, when it tries to mount the computer just shuts down or sometimes breaks and i have to reset...
I have tried to edit the fstab based on the information i get from running the tool hwinfo (hardware information) here is the information :

    [Created at block.226]
  UDI: /org/freedesktop/Hal/devices/storage_model_DVDRAM_GH20NS10
  Unique ID: twPO.NYm9QTAFVy1
  Parent ID: M71A.MQef92r1XgF
  SysFS ID: /block/sr0
  SysFS BusID: 1:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:07.0/host1/target1:0:0/1:0:0:0
  Hardware Class: cdrom
  Model: "HL-DT-ST DVDRAM GH20NS10"
  Vendor: "HL-DT-ST"
  Device: "DVDRAM GH20NS10"
  Revision: "EL00"
  Driver: "sata_nv", "sr"
  Driver Modules: "sata_nv"
  Device File: /dev/sr0 (/dev/sg0)
  Device Files: /dev/sr0, /dev/scd0, /dev/disk/by-path/pci-0000:00:07.0-scsi-1:0:0:0, /dev/cdrom2
  Device Number: block 11:0 (char 21:0)
  Features: DVD
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (IDE interface)


And i have edited the fstab to look like this:

/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=18dc83a6-6340-41d9-b8bc-b1d55f221985 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=b12b6747-a8d8-41f2-83aa-bb45a4a17fba /boot           ext3    relatime        0       2
# /dev/sda4
UUID=ccc6e738-383c-440b-9e13-9e865ed35f7b /home           ext3    relatime        0       2
# /dev/sda1
UUID=c788c2c6-499b-4bb4-8d8b-31d4a56de379 none            swap    sw              0       0
/dev/sg0       /dev/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

here it is ... still dvd doenst mount... :confused:



here is my computer specs:

Ubuntu 8.04 (hardy)
2.6.24-21-generic 4.2.4 (x86_64-linux-gnu)

AMD Athlon(tm) 64 X2 Dual Core Processor 5000+

I have also seen the bios for any problem relating the sata drive but everything seems to be normal...

Really need some help whit this...:(

---

