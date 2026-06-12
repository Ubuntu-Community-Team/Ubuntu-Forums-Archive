---
title: "USB camera mount"
date: 2005-04-28
forum: Hardware &amp; Laptops
---

### Post by foxy123 on 2005-04-28
I have a JVC camcorder which have a flash mamory card for still images. It mounted of under Ubuntu. But yesterday due to some mistakes the permissions for /usr was messed up. I restored it as I could (see the thread for details [http://ubuntuforums.org/showthread.php?t=29967)](http://ubuntuforums.org/showthread.php?t=29967)). Anyway, now I cannot access the camera. It looks like it mounts but either something wrong with the permissions or else.

This is my dmesg:

```
usb 1-1: new full speed USB device using uhci_hcd and address 5
scsi3 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
  Vendor: JVC       Model: DV CAMERA         Rev: 0000
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sda: 15680 512-byte hdwr sectors (8 MB)
sda: Write Protect is off
sda: Mode Sense: 00 32 02 00
sda: assuming drive cache: write through
SCSI device sda: 15680 512-byte hdwr sectors (8 MB)
sda: Write Protect is off
sda: Mode Sense: 00 32 02 00
sda: assuming drive cache: write through
 /dev/scsi/host3/bus0/target0/lun0: p1
Attached scsi removable disk sda at scsi3, channel 0, id 0, lun 0
usb-storage: device scan complete
``` 

I do not see anything wrong here. However, I do not see it in my media:/ in Konquerer. I've got some SUNVOL which is sda1, but if I try to open it I have

```
Could not mount device
The reported error was:
mount can't find /dev/sda1 in /etc/fstab or /ets/mtab
``` 

however, it has not needed an entry in fstab before...

actually i can mount it manually, but i wonder why it does not automount anymore?

---

### Post by QuantumCowboy on 2005-04-28
no idea why it wont automount anymore, but after editing fstab it should work.

/dev/sda1  /media/camera  auto  defaults,auto,unhide,user   0   0

-QC

---

