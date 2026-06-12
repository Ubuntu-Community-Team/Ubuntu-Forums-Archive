---
title: "Optiarc DVD RW AD-7190A  DVD -R DL write"
date: 2008-06-09
forum: Hardware
---

### Post by mlloewen on 2008-06-09
Here is and excerpt from my "hwinfo" as I can see and you can too that the drive does not support DVD -R DL.  Yet if you goto the optiarc web site it says it does support -R DL.  Ubuntu 8.04 64 bit.

   -Is there a work around to force it to work?  
   -Also do you know if there is a way to use sonys firmware upgrade in linux? Using WINE I get an error message saying check with the vendor.
   -so far playing DVDs has worked well(including DL) except for one yet DVDL it does not mount the DVD. 

Thanks 

SCSI 600.0: 10602 CD-ROM (DVD)
  [Created at block.226]
  UDI: /org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_7190A
  Unique ID: twPO.64MQiqqpmV8
  Parent ID: 8otl.m2ww_NHLTK1
  SysFS ID: /block/sr0
  SysFS BusID: 6:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:04.0/host6/target6:0:0/6:0:0:0
  Hardware Class: cdrom
  Model: "Optiarc DVD RW AD-7190A"
  Vendor: "Optiarc"
  Device: "DVD RW AD-7190A"
  Revision: "1.01"
  Driver: "pata_amd", "sr"
  Driver Modules: "pata_amd"
  Device File: /dev/sr0 (/dev/sg1)
  Device Files: /dev/sr0, /dev/scd0, /dev/disk/by-path/pci-0000:00:04.0-scsi-0:0:0:0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw
  Device Number: block 11:0 (char 21:1)
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL, DVDRAM
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #34 (IDE interface)
  Drive Speed: 12

---

