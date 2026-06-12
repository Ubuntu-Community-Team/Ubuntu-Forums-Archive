---
title: "USB Flash Drive Error"
date: 2005-01-31
forum: Hardware &amp; Laptops
---

### Post by timothyarnold85 on 2005-01-31
I was trying to mount a USB flash drive, and ubuntu wasn't recognizing it, so I checked dmesg and found this:

usb 3-5: new high speed USB device using address 12
usb 3-5: device not accepting address 12, error -71
usb 3-5: new high speed USB device using address 13
usb 3-5: device not accepting address 13, error -71


Does anyone have any idea why this is happening? I've tried two different drives, too.

---

### Post by ptd on 2005-03-16
[QUOTE=timothyarnold85]I was trying to mount a USB flash drive, and ubuntu wasn't recognizing it, so I checked dmesg and found this:

usb 3-5: new high speed USB device using address 12
usb 3-5: device not accepting address 12, error -71
usb 3-5: new high speed USB device using address 13
usb 3-5: device not accepting address 13, error -71


Does anyone have any idea why this is happening? I've tried two different drives, too.[/QUOTE]

I have experienced the same thing - I am using a completely up to date Hoary install.  I can get the drive to be recognized on occasion, if I remove and insert it again (or several times.)  When it does decide to work, this is what shows up in dmesg:

usb 4-3: new high speed USB device using ehci_hcd and address 16
scsi3 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 16
usb-storage: waiting for device to settle before scanning
  Vendor: I-Stick2  Model: IntelligentStick  Rev: 2.00
  Type:   Direct-Access                      ANSI SCSI revision: 02
sda: Unit Not Ready, sense:
Current : sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sda : READ CAPACITY failed.
sda : status=1, message=00, host=0, driver=08
Current sd: sense key Unit Attention
Additional sense: Not ready to ready change, medium may have changed
sda: test WP failed, assume Write Enabled
sda: assuming drive cache: write through
SCSI device sda: 1023488 512-byte hdwr sectors (524 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 1023488 512-byte hdwr sectors (524 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
 /dev/scsi/host3/bus0/target0/lun0: unknown partition table
Attached scsi removable disk sda at scsi3, channel 0, id 0, lun 0
usb-storage: device scan complete
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

---

### Post by lorap on 2005-03-16
hi buddy!
try this:

create flash directory:

sudo mkdir /media/flash

then write this:

sudo mount /dev/sr0(or sda0 or sda1 if hoary) /media/flash -t vfat -o umask=000

let me know if it helped.
pavel

---

### Post by ptd on 2005-03-16
[QUOTE=lorap]hi buddy!
try this:

create flash directory:

sudo mkdir /media/flash

then write this:

sudo mount /dev/sr0(or sda0 or sda1 if hoary) /media/flash -t vfat -o umask=000

let me know if it helped.
pavel[/QUOTE]

Inserted flash drive, made sure previously mentioned error occurred in dmesg:

usb 4-3: new high speed USB device using ehci_hcd and address 20
usb 2-1: new full speed USB device using uhci_hcd and address 26
usb 2-1: device descriptor read/64, error -71
usb 2-1: device descriptor read/64, error -71
usb 2-1: new full speed USB device using uhci_hcd and address 27
usb 2-1: device descriptor read/64, error -71
usb 2-1: device descriptor read/64, error -71


Results of "sudo mount /dev/sda1 /media/flash/ -t vfat -o umask=000":

mount: special device /dev/sda1 does not exist

---

### Post by nemesa on 2005-03-16
I had the same problem... The linux-image-2.6.10-4-386 solved it.
Which kernel do you use?

---

### Post by lorap on 2005-03-16
hi friend!
you should have tried not sda0 or 1 but sr0.i'm using warty and this device works with usb.try it again with sr0 and scd0.
pavel

---

### Post by ptd on 2005-03-16
[QUOTE=nemesa]I had the same problem... The linux-image-2.6.10-4-386 solved it.
Which kernel do you use?[/QUOTE]

I have tried it just today on:

linux-image-2.6.10-5-386
linux-image-2.6.10-5-686

---

### Post by lorap on 2005-03-16
hi friend!
you should have tried not sda0 or 1 but sr0.i'm using warty and this device works with usb.try it again with sr0 and scd0.
pavel

---

### Post by ptd on 2005-03-16
[QUOTE=lorap]hi friend!
you should have tried not sda0 or 1 but sr0.i'm using warty and this device works with usb.try it again with sr0 and scd0.
pavel[/QUOTE]

Doesn't work.  As you can see in my previous post, when it DOES work, the drive gets mounted as /dev/sda:

[QUOTE=ptd]Attached scsi removable disk sda at scsi3, channel 0, id 0, lun 0[/QUOTE]

---

### Post by ptd on 2005-03-17
See Bug #7633 - this looks the same as my problem.

[https://bugzilla.ubuntu.com/show_bug.cgi?id=7633](https://bugzilla.ubuntu.com/show_bug.cgi?id=7633)

---

### Post by ptd on 2005-03-22
An update to linux-image-2.6.10-5-686 today (to version 2.6.10-29) seems to have fixed the problem for me.  My flash drives are detected and mounted every time they are inserted now.  Can anyone else with the probelm confirm that it works for them now?

(This is on a Hoary install, not Warty)

---

### Post by hien on 2005-04-01
hello all,
thanks, it worked for me. 
fyi: i'm using warty and mounted my usb flash drive as sda1.
-H.

---

