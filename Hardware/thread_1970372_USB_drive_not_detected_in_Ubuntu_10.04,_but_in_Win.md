---
title: "USB drive not detected in Ubuntu 10.04, but in Windows"
date: 2012-05-01
forum: Hardware
---

### Post by dtordrup on 2012-05-01
Hello,

I have an internal eIDE drive (WD Caviar, 13GB) which is probably 10 years old. I have been using it as a normal eIDE drive, with a ribbon cable inside a machine running Ubuntu 9.04 where it was recognized and mounted fine. I took the drive out and sold that computer, and am now trying to extract data from the HD using a USB IDE adaptor. However, when I try to connect the drive to Ubuntu 10.04 (on my current laptop) through USB it is not recognized. Outputs:

sudo fdisk -l
* lists my internal drive and other USB HDs fine

lsusb
* does not list the drive, but other USB HDs also fine

ls /dev/sd*
* does not list the drive, either, but other HDs and USB HDs fine

Other information:
* The drive can be connected via USB to Windows XP Pro on another computer (reads and writes fine)
* I have tried all reasonable jumper settings but no luck
* I have my laptop boot order set to USB first, but on booting with the HD connected, it does not seem to recognize the HD
* I have "USB Legacy mode" enabled in BIOS

So this leads me to believe, somehow, my laptop (rather old Compaq N610c) does not like the drive. Any thoughts on this?

Best,

David

---

### Post by dtordrup on 2012-05-01
Though I did reboot a couple of times without success yesterday, when I tried again today everything worked as it should :confused:

> **dtordrup said:**
> Hello,

I have an internal eIDE drive (WD Caviar, 13GB) which is probably 10 years old. I have been using it as a normal eIDE drive, with a ribbon cable inside a machine running Ubuntu 9.04 where it was recognized and mounted fine. I took the drive out and sold that computer, and am now trying to extract data from the HD using a USB IDE adaptor. However, when I try to connect the drive to Ubuntu 10.04 (on my current laptop) through USB it is not recognized. Outputs:

sudo fdisk -l
* lists my internal drive and other USB HDs fine

lsusb
* does not list the drive, but other USB HDs also fine

ls /dev/sd*
* does not list the drive, either, but other HDs and USB HDs fine

Other information:
* The drive can be connected via USB to Windows XP Pro on another computer (reads and writes fine)
* I have tried all reasonable jumper settings but no luck
* I have my laptop boot order set to USB first, but on booting with the HD connected, it does not seem to recognize the HD
* I have "USB Legacy mode" enabled in BIOS

So this leads me to believe, somehow, my laptop (rather old Compaq N610c) does not like the drive. Any thoughts on this?

Best,

David

---

