---
title: "USB Drive bricked?"
date: 2009-04-14
forum: Hardware
---

### Post by HuXu on 2009-04-14
I got a cool lil HP Blackbird 002 USB drive and well whenever I would plug it into Windows XP (in VirtualBox) it would identify its self as a JetFlash drive or something and well now I had some problems with it recently staying in the USB port and I messed it up.  It now is recognized as an Alcor USB and it will mount (in Windows) but asks to be formatted and then says it cant format it.  In Ubuntu it doesnt even show up and dmesg:

```

[ 6196.560541] usb 8-2: new high speed USB device using ehci_hcd and address 4
[ 6196.698689] usb 8-2: configuration #1 chosen from 1 choice
[ 6196.701452] scsi7 : SCSI emulation for USB Mass Storage devices
[ 6196.702277] usb-storage: device found at 4
[ 6196.702279] usb-storage: waiting for device to settle before scanning
[ 6201.701049] usb-storage: device scan complete
[ 6201.702317] scsi 7:0:0:0: Direct-Access     Generic  USB Flash Disk   7.76 PQ: 0 ANSI: 2
[ 6201.706511] sd 7:0:0:0: [sdb] 1 512-byte hardware sectors (0 MB)
[ 6201.707599] sd 7:0:0:0: [sdb] Write Protect is off
[ 6201.707611] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 6201.707618] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 6201.710849] sd 7:0:0:0: [sdb] 1 512-byte hardware sectors (0 MB)
[ 6201.715026] sd 7:0:0:0: [sdb] Write Protect is off
[ 6201.715041] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 6201.715047] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 6201.716137]  sdb:<3>end_request: I/O error, dev sdb, sector 0
[ 6201.717198] __ratelimit: 11 callbacks suppressed
[ 6201.717205] Buffer I/O error on device sdb, logical block 0
[ 6201.720959] end_request: I/O error, dev sdb, sector 0
[ 6201.720971] Buffer I/O error on device sdb, logical block 0
[ 6201.724055] end_request: I/O error, dev sdb, sector 0
[ 6201.724065] Buffer I/O error on device sdb, logical block 0
[ 6201.730327] end_request: I/O error, dev sdb, sector 0
[ 6201.730341] Buffer I/O error on device sdb, logical block 0
[ 6201.751442] end_request: I/O error, dev sdb, sector 0
[ 6201.751457] Buffer I/O error on device sdb, logical block 0
[ 6201.751484] ldm_validate_partition_table(): Disk read failed.
[ 6201.752819] end_request: I/O error, dev sdb, sector 0
[ 6201.752832] Buffer I/O error on device sdb, logical block 0
[ 6201.753817] end_request: I/O error, dev sdb, sector 0
[ 6201.753827] Buffer I/O error on device sdb, logical block 0
[ 6201.754814] end_request: I/O error, dev sdb, sector 0
[ 6201.754821] Buffer I/O error on device sdb, logical block 0
[ 6201.755815] end_request: I/O error, dev sdb, sector 0
[ 6201.755822] Buffer I/O error on device sdb, logical block 0
[ 6201.755842] Dev sdb: unable to read RDB block 0
[ 6201.757060] end_request: I/O error, dev sdb, sector 0
[ 6201.757068] Buffer I/O error on device sdb, logical block 0
[ 6201.758188] end_request: I/O error, dev sdb, sector 0
[ 6201.759218] end_request: I/O error, dev sdb, sector 0
[ 6201.760186] end_request: I/O error, dev sdb, sector 0
[ 6201.760205]  unable to read partition table
[ 6201.767558] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 6201.768916] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 6201.872629] end_request: I/O error, dev sdb, sector 0
[ 6201.873928] end_request: I/O error, dev sdb, sector 0
[ 6202.099197] end_request: I/O error, dev sdb, sector 0
[ 6202.100575] end_request: I/O error, dev sdb, sector 0
[ 6202.103323] end_request: I/O error, dev sdb, sector 0
[ 6204.015829] end_request: I/O error, dev sdb, sector 0
[ 6204.016799] end_request: I/O error, dev sdb, sector 0


```

What would be something I could try?

---

### Post by jrz on 2009-07-03
I just encountered the same situation, on a USB drive containing over 200GB's of data, and am becoming quite upset with Ubuntu's support of USB. It appears to be an area that gets little or no attention, and bug reports eventually fade away due to no activity. The problem with USB seems to go back many years, and often googling I see links that are in relation to Ubuntu 6.06 having USB problems and instead of getting better the problems appear to be worsening. Until last night I had been able to eventually get drives to mount and transfer data by rebooting, and mounting and remounting until the drive would be recognized, but the problem now is the same as yours and even Gparted will not recognize the drive. Sadly I had reformatted my drives to ext3 and can no longer use WinXP to recover my data. Previously, when using ntfs I could always boot WinXP and access my drives. 

I am having a difficult time deciding to stay with Ubuntu or return to WinXP as my files are too important to be kept on an OS that can't be trusted. 

I've not yet found a location where help or assistance in recovering from major problems such as this can be found, and if you have any success in this area please note it here. I have 9 more USB drives and am at a standstill until I can find a way to save their content and return to ntfs.

---

### Post by triffle on 2009-07-06
Hey Everyone... I was having similar problem. Mine started when I created a "usb startup disk" so after alot of forum searching a googling... i finally found a fix that worked for me.... Here is the link... [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) please see after installing for the fix.

I am not really sure if this will work for you but check /etc/fstab from terminal

sudo gedit /etc/fstab

check and see if you see a line towards the bottom of the page like this 

/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

if so just put a comment in front of the line like this

#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

save and close

What this is doing i think is telling ubuntu that your usb drive is your cdrom0.

Hopefully this will work for you, it seems like you have been kinda sitting in the dark on this. If not not really sure what to do... Bump

Much Thanks to the ubuntu community...

---

### Post by jrz on 2009-07-07
My USB drives have no entry in fstab, and usually mount with /media/.hal-mtab identifying them. The drive in trouble now appears to have corrupted sector 0 and I've got it connected showing an entry in /dev as sdb1 which is what it usually mounts as but it will not mount any longer.

---

