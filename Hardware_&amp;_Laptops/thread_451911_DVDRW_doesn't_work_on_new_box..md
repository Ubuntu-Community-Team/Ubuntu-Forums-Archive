---
title: "DVDRW doesn't work on new box."
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by Red Knuckles on 2007-05-22
New sort of problem for me. I just built my 1st computer. :

ASUS M2NPV-VM      motherboard
AMD Athlon64 X2 4800+ processor
2 GB RAM DDR2 800mhz
320 GB IDE HD abd 320 GB SATA HD
Pioneer DVR-112D      DVDRW

Problem is I can't get the DVDRW to work properly. I allegedly successfully downloaded as ISO 9660 OS CD according to K3B [Success!] but when I try to boot it in any mode I end up with 'kernel panic'. Part of my struggle is where to start to problem solve this??? What info to gather and where??? I have an older CD-ROM I can pop in the box which will and in fact has installed OS's on my new box. The CD's it's installing are burned on an externel DVDRW I have so that all works over many Linux operating systems. I need some help in getting started on this in terms of info gathering information and what documentation to read. Unless of course it's something simple I haven't learned yet [Likely!!!].:(

---

### Post by Red Knuckles on 2007-05-23
Some info:

from /etc/fstab:

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

but I don't have a floppy drive installed on this computer?

$ hwinfo --cdrom
32: IDE 03.0: 10602 CD-ROM (DVD)
[Created at block.222]
UDI: /org/freedesktop/Hal/devices/storage_model_PIONEER_DVD_RW_DVR_112D
Unique ID: cBQ5.4giZDOab2vB
Parent ID: qnJ_.os+qg5s0h31
SysFS ID: /block/hdd
SysFS BusID: 1.1
SysFS Device Link: /devices/pci0000:00/0000:00:0d.0/ide1/1.1
Hardware Class: cdrom
Model: "PIONEER DVD-RW DVR-112D"
Vendor: "PIONEER"
Device: "DVD-RW DVR-112D"
Driver: "AMD_IDE", "ide-cdrom"
Driver Modules: "amd74xx", "ide_cd"
Device File: /dev/hdd
Device Files: /dev/hdd, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw, /dev/disk/by-path/pci-0000:00:0d.0-ide-1:1
Device Number: block 22:64
Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL
Size: 0 sectors a 512 bytes
Drive status: no medium
Config Status: cfg=new, avail=yes, need=no, active=unknown
Attached to: #19 (IDE interface)
Drive Speed: 40

33: SCSI 00.0: 10602 CD-ROM
[Created at block.222]
UDI: /org/freedesktop/Hal/devices/storage_serial_DVDRW_USB1008UI_11210521600000006504_0_0
Unique ID: cLrx.hurpsexLtv0
Parent ID: Xuit.05q+qh2wtIB
SysFS ID: /block/sr0
SysFS BusID: 0:0:0:0
SysFS Device Link: /devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2:1.0/host0/target0:0:0/0:0:0:0
Hardware Class: cdrom
Model: "DVDRW USB1008UI"
Vendor: usb 0x046e "DVDRW"
Device: usb 0x3002 "USB1008UI"
Revision: "0056"
Serial ID: "11210521600000006504"
Driver: "usb-storage", "sr"
Driver Modules: "usb_storage"
Device File: /dev/sr0 (/dev/sg1)
Device Files: /dev/sr0, /dev/scd0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw, /dev/disk/by-id/usb-DVDRW_USB1008UI_11210521600000006504-0:0, /dev/disk/by-path/pci-0000:00:0b.1-usb-0:2:1.0-scsi-0:0:0:0
Device Number: block 11:0 (char 21:1)
Features: CD-R, CD-RW, DVD-R, DVD-RW, DVD+R, DVD+RW, Hotpluggable
Speed: 480 Mbps
Module Alias: "usb:v046Ep3002d0103dc00dsc00dp00ic08isc06ip50"
Driver Info #0:
Driver Status: libusual is active
Driver Activation Cmd: "modprobe libusual"
Drive status: no medium
Config Status: cfg=new, avail=yes, need=no, active=unknown
Attached to: #18 (USB Controller)
Drive Speed: 40

I'm wondering is there a simple config command that will get it working? Do I nee to install/add a driver somewhere? And does any of this address why when trying to use ISO 9660 Live/Install Cd's does it end in 'kernel panic':(

---

### Post by Red Knuckles on 2007-05-23
This is weird. I currently have disconnected my external DVDRW. Then I opened a new slot in my Cooler Master Centurion 5 case and added my old Lite ON CDROM. So I now have the Pioneer problem child DVDRW set as 2nd IDE Master and Lite On CDROM set as 2nd IDE Slave [1st IDE is 320GB HD]. In my BIOS I set the Pioneer DVDRW as 1st in CDROM list with boot order set to boot CDROM 1st [as it has been all along]. Now the Pioneer DVDRW WILL boot ISO CD's! I tested both Ubuntu and Sabayon CD's. Booted and opened no problem. Then I disconnect the Lite On CDROM and the the Pioneer DVDRW continues to boot ISO's. I turned off power supply twice and it still boots ISO's. Then I get brave turn power off and unplug DVDRW then plug it back in and it's broke again. Went through the process again. ie. Hook up CDROM get ISO's to boot with DVDRW then unhook CDROM and test ISO's again and still working. For now at least. Huh???????

/etc/fstab:

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

Here is results of hwinfo --cdrom with BOTH devices connected:

$ hwinfo --cdrom
32: IDE 02.0: 10602 CD-ROM (DVD)
[Created at block.222]
UDI: /org/freedesktop/Hal/devices/storage_model_PIONEER_DVD_RW_DVR_112D
Unique ID: 90A1.4giZDOab2vB
Parent ID: qnJ_.os+qg5s0h31
SysFS ID: /block/hdc
SysFS BusID: 1.0
SysFS Device Link: /devices/pci0000:00/0000:00:0d.0/ide1/1.0
Hardware Class: cdrom
Model: "PIONEER DVD-RW DVR-112D"
Vendor: "PIONEER"
Device: "DVD-RW DVR-112D"
Driver: "AMD_IDE", "ide-cdrom"
Driver Modules: "amd74xx", "ide_cd"
Device File: /dev/hdc
Device Files: /dev/hdc, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw, /dev/disk/by-path/pci-0000:00:0d.0-ide-1:0
Device Number: block 22:0
Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL
Size: 1431976 sectors a 512 bytes
Config Status: cfg=new, avail=yes, need=no, active=unknown
Attached to: #19 (IDE interface)
Drive Speed: 32
Volume ID: "Ubuntu 7.04 amd64"
Application: "MKISOFS ISO 9660/HFS FILESYSTEM BUILDER & CDRECORD CD-R/DVD CREATOR (C) 1993 E.YOUNGDALE (C) 1997 J.PEARSON/J.SCHILLING"
Creation date: "2007041515512100"
El Torito info: platform 0, bootable
Boot Catalog: at sector 0x0113
Media: none starting at sector 0x010c
Load: 2048 bytes

Wonder how I can make this piece of bleep Pioneer DVDRW work permanently???:(

---

