---
title: "USB Card Reader Mount Problem (superblock problem)"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by Paulo Wageck on 2005-09-23
Hello...

I have been fighting with this SD card reader and linux...  ](*,) 

# mount -t vfat /dev/sdd /media/sdcard
mount: block device /dev/sdd is write-protected, mounting read-only
mount: /dev/sdd: can't read superblock

Please help.

What I know by now:

The whole SD card is one partition.... (sdd) in my case...

Due to a problem beyond my mind it does't read properly sdd when mounting...

I have heard about a unusual device list i can add my SD card reader... but I dunno how..... like compiling the kernel with a changed unusual_devs.h

 cat /proc/bus/usb/devices

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=08ca ProdID=3103 Rev= 1.00
S:  Product=Generic
S:  SerialNumber=SDC/MMC
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=05 Prot=50 Driver=usb-storage
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms



dmesg

usb 1-1: new full speed USB device using uhci_hcd and address 5
scsi7 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
  Vendor: Generic   Model: SDC/MMC           Rev: 1.10
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sdd: 248320 512-byte hdwr sectors (127 MB)
sdd: Write Protect is on
sdd: Mode Sense: 00 12 00 80
sdd: assuming drive cache: write through
SCSI device sdd: 248320 512-byte hdwr sectors (127 MB)
sdd: Write Protect is on
sdd: Mode Sense: 00 12 00 80
sdd: assuming drive cache: write through
 /dev/scsi/host7/bus0/target0/lun0:SCSI error : <7 0 0 0> return code = 0x10070000
end_request: I/O error, dev sdd, sector 0
Buffer I/O error on device sdd, logical block 0
SCSI error : <7 0 0 0> return code = 0x10070000
end_request: I/O error, dev sdd, sector 0
Buffer I/O error on device sdd, logical block 0
 unable to read partition table
Attached scsi removable disk sdd at scsi7, channel 0, id 0, lun 0
usb-storage: device scan complete
SCSI error : <7 0 0 0> return code = 0x10070000
end_request: I/O error, dev sdd, sector 0
Buffer I/O error on device sdd, logical block 0
SCSI error : <7 0 0 0> return code = 0x10070000
end_request: I/O error, dev sdd, sector 8
Buffer I/O error on device sdd, logical block 1
SCSI error : <7 0 0 0> return code = 0x10070000
end_request: I/O error, dev sdd, sector 16
Buffer I/O error on device sdd, logical block 2
SCSI error : <7 0 0 0> return code = 0x10070000
end_request: I/O error, dev sdd, sector 24
Buffer I/O error on device sdd, logical block 3
SCSI error : <7 0 0 0> return code = 0x10070000
end_request: I/O error, dev sdd, sector 32
Buffer I/O error on device sdd, logical block 4




THANKS IN ADVANCE
 :grin:

---

### Post by Paulo Wageck on 2005-09-30
I have managed to make it work under XP VMWare machine... with the usb module unloaded on linux....

I know for sure it is a Linux problem!!!!

Anyone knows how to add a device to unusual_dev.s ??
How it works???

---

### Post by TheAreopagite on 2005-10-02
I had a similar 'cant read superblock' problem with a USB flash memory stick.

I never did work out exactly what was wrong; because whatever it was, installing breezy fixed it.

You could try burning a breezy live disk and see if that mounts your card reader.

---

### Post by Paulo Wageck on 2005-10-02
Yeah.... thanks for the reply...

I could mount it on a debian system with kernel 2.4.....;) 

It might be a kernel problem or something like that....:D 

I tried to install breezy before hoary..... but the system crashed during the install so I am stick with hoary.... ](*,) 

I will try the live CD... let´s see if it works... I will keep the thread updated... It seens to be the same king of problem that avoids some mac users to use ipod on the linux system... it also affects some memory sticks... id you partition your memory stick... you can mount them as sdd1, sdd2 or whatever... if you only have one large partition it seens to have a problem rearing and recognizing one large partition... (superblock stuff.....).... 

I have read about disabling EFS partition supoort on the kernel.... (ok) and adding the device to the unusual_devs.h (source).... it should work after installing the new kernel... but i dunno the syntax to do this... 

Meanwhile I am using the virtual machine to keep my SD card reader working... 

Cheers,

---

