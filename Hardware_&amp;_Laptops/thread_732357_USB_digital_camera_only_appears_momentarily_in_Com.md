---
title: "USB digital camera only appears momentarily in Computer directory"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by cebif on 2008-03-22
I have a Kyocera Finecam s3r USB camera. When I plug it in with the Computer directory open it appears momentarily for about one second then vanishes. I tried the mount command but I cannot see it anywhere in the list. It does not matter what socket I plug it into. 
The camera is shown in Device Manager but it is shown as not mounted and has automount enabled.
Help would be really appreciated.

---

### Post by Samurai Penguin on 2008-03-23
not sure if any of this will help or not ...

Code:

tail -f /var/log/messages

THEN plug your camera in and watch the terminal screen. The device file of the camera should appear. It will typically be something like sdXY where X is a letter and Y is a number, (examples: sda1 sdb5 sdc2)
Take a look in the /media directory to see if there is a mount point for your camera. If not make one:
Code:

sudo mkdir /media/camera

Then mount the camera
Code:

sudo mount /dev/sda1 /media/camera

Then just change into the mount directory (in this case /media/camera) and browse the photos. Copy a few to your home directory:
Code:

sudo cp filenames /home/username

---

### Post by cebif on 2008-03-23
Thanks for you're quick reply
I tried the commands you gave. This is what I got for the first command before and after the camera was plugged in:
greg@greg-desktop:~$ tail -f /var/log/messages
Mar 23 19:37:24 greg-desktop kernel: [39293.088420] end_request: I/O error, dev sdb, sector 20
Mar 23 19:37:24 greg-desktop kernel: [39293.105398] end_request: I/O error, dev sdb, sector 19
Mar 23 19:37:24 greg-desktop kernel: [39293.122386] end_request: I/O error, dev sdb, sector 20
Mar 23 19:37:24 greg-desktop kernel: [39293.139374] end_request: I/O error, dev sdb, sector 19
Mar 23 19:37:24 greg-desktop kernel: [39293.156361] end_request: I/O error, dev sdb, sector 20
Mar 23 19:37:24 greg-desktop kernel: [39293.173349] end_request: I/O error, dev sdb, sector 19
Mar 23 19:37:24 greg-desktop kernel: [39293.190336] end_request: I/O error, dev sdb, sector 19
Mar 23 19:37:24 greg-desktop kernel: [39293.207323] end_request: I/O error, dev sdb, sector 20
Mar 23 19:41:14 greg-desktop kernel: [39524.178836] end_request: I/O error, dev sdb, sector 19
Mar 23 19:42:06 greg-desktop kernel: [39575.863054] usb 1-3: USB disconnect, address 8
Mar 23 19:47:23 greg-desktop kernel: [39892.444713] usb 2-3: new full speed USB device using ohci_hcd and address 2
Mar 23 19:47:23 greg-desktop kernel: [39892.647747] usb 2-3: configuration #1 chosen from 1 choice
Mar 23 19:47:23 greg-desktop kernel: [39892.650752] scsi7 : SCSI emulation for USB Mass Storage devices
Mar 23 19:47:28 greg-desktop kernel: [39897.658939] scsi 7:0:0:0: Direct-Access     Kyocera  Finecam S3R      1.00 PQ: 0 ANSI: 2
Mar 23 19:47:28 greg-desktop kernel: [39897.680907] sd 7:0:0:0: [sdb] 29121 512-byte hardware sectors (15 MB)
Mar 23 19:47:28 greg-desktop kernel: [39897.687903] sd 7:0:0:0: [sdb] Write Protect is off
Mar 23 19:47:28 greg-desktop kernel: [39897.713882] sd 7:0:0:0: [sdb] 29121 512-byte hardware sectors (15 MB)
Mar 23 19:47:28 greg-desktop kernel: [39897.720879] sd 7:0:0:0: [sdb] Write Protect is off
Mar 23 19:47:28 greg-desktop kernel: [39897.720892]  sdb: sdb1
Mar 23 19:47:28 greg-desktop kernel: [39897.732992] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Mar 23 19:47:28 greg-desktop kernel: [39897.733051] sd 7:0:0:0: Attached scsi generic sg1 type 0

At this point it seems to lose communication. This probably corresponds to when it vanishes from view in the Computer diurectory.
  
Mar 23 19:47:28 greg-desktop kernel: [39897.921723] end_request: I/O error, dev sdb, sector 29120
Mar 23 19:47:28 greg-desktop kernel: [39897.921730] printk: 302 messages suppressed.
Mar 23 19:47:28 greg-desktop kernel: [39897.938711] end_request: I/O error, dev sdb, sector 29120
Mar 23 19:47:28 greg-desktop kernel: [39897.955697] end_request: I/O error, dev sdb, sector 29112

The messages carry on similar to this righr up to this one when I unplug the camera.

Mar 23 19:47:31 greg-desktop kernel: [39901.097367] end_request: I/O error, dev sdb, sector 0
Mar 23 19:48:28 greg-desktop kernel: [39957.238890] usb 2-3: USB disconnect, address 2
Mar 23 20:02:41 greg-desktop -- MARK --

I looked in the /media and there was no camera so I did:

greg@greg-desktop:~$ sudo mkdir /media/camera
[sudo] password for greg:
greg@greg-desktop:~$ sudo mount /dev/sdb1 /media/camera
mount: you must specify the filesystem type
greg@greg-desktop:~$ sudo mount -t fat /dev/sdb1 /media/camera
mount: unknown filesystem type 'fat'
mount: maybe you meant 'vfat'?
greg@greg-desktop:~$ sudo mount -t vfat /dev/sdb1 /media/camera
mount: /dev/sdb1: can't read superblock
greg@greg-desktop:~$ 

So it could not read superblock. I'm not certain what that means
It could look like a faulty SD memory memory card but this camera was recognized when I had Windows XP and it is still recognized with BeosR5.05 Bone.
I was not certain what type of fat file system it had. I thought it might be 16 bit that is why I only specified the "-t fat " first time and got the " unknown filesystem type 'fat' message. I thought 16 bit was just fat and 32 bit was vfat.
Any ideas thanks

---

