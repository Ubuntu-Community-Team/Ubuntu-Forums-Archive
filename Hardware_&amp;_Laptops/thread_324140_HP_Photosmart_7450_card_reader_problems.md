---
title: "HP Photosmart 7450 card reader problems"
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by generice_genus on 2006-12-23
Hey I am having problems with the HP Photosmart 7450 card reader, when I insert a card it is not automatically mounted. [This thread]("http://ubuntuforums.org/showthread.php?p=1922601#post1922601") is for someone else having the same problem.

I can mount the drive after following this procedure:
1. Insert card
2. open computer:// (Places->Computer)
3. Wait for for light on card reader to stop blinking
4. Double click on "HP Photosmart 7400"
5. A dialog window will now appear saying "opening HP Photosmart 7400, wait for this to finish and
the file browser window will switch to the root directory (i.e. "/")
6. The card is now mounted at /media/usbdisk

I was hoping somebody could help me to get the card reader to work like a standard removable device (i.e. be automounted when a card is inserted) using a UDEV rule or whatever is needed. 

When a card is inserted the following is output to /var/log/messages:
> Dec 23 13:47:59 family kernel: [ 6936.759634] SCSI device sda: 1951744 512-byte hdwr sectors (999 MB)
Dec 23 13:47:59 family kernel: [ 6936.772830] sda: Write Protect is off
Dec 23 13:47:59 family kernel: [ 6936.790605] SCSI device sda: 1951744 512-byte hdwr sectors (999 MB)
Dec 23 13:47:59 family kernel: [ 6936.800592] sda: Write Protect is off
Dec 23 13:47:59 family kernel: [ 6936.800812]  sda: unknown partition table
Dec 23 13:48:03 family kernel: [ 6940.552364] sd 0:0:0:0: SCSI error: return code = 0x8000002
Dec 23 13:48:03 family kernel: [ 6940.552384] sda: Current: sense key: Medium Error
Dec 23 13:48:03 family kernel: [ 6940.552390]     Additional sense: Read error - loss of streaming
Dec 23 13:48:03 family kernel: [ 6940.552402] end_request: I/O error, dev sda, sector 1951616
Dec 23 13:48:06 family kernel: [ 6944.117096] sd 0:0:0:0: SCSI error: return code = 0x8000002
Dec 23 13:48:06 family kernel: [ 6944.117114] sda: Current: sense key: Medium Error
Dec 23 13:48:06 family kernel: [ 6944.117120]     Additional sense: Read error - loss of streaming
Dec 23 13:48:06 family kernel: [ 6944.117132] end_request: I/O error, dev sda, sector 1951616
Dec 23 13:48:10 family kernel: [ 6947.665898] sd 0:0:0:0: SCSI error: return code = 0x8000002
Dec 23 13:48:10 family kernel: [ 6947.665917] sda: Current: sense key: Medium Error
Dec 23 13:48:10 family kernel: [ 6947.665922]     Additional sense: Read error - loss of streaming
Dec 23 13:48:10 family kernel: [ 6947.665935] end_request: I/O error, dev sda, sector 1951736
Dec 23 13:48:14 family kernel: [ 6951.231681] sd 0:0:0:0: SCSI error: return code = 0x8000002
Dec 23 13:48:14 family kernel: [ 6951.231701] sda: Current: sense key: Medium Error
Dec 23 13:48:14 family kernel: [ 6951.231706]     Additional sense: Read error - loss of streaming
Dec 23 13:48:14 family kernel: [ 6951.231719] end_request: I/O error, dev sda, sector 1951736


After double-clicking "HP Photosmart 7400" in computer:// the following is output
> 
Dec 23 13:50:15 family kernel: [ 7072.494490] sd 0:0:0:0: SCSI error: return code = 0x8000002
Dec 23 13:50:15 family kernel: [ 7072.494510] sda: Current: sense key: Medium Error
Dec 23 13:50:15 family kernel: [ 7072.494515]     Additional sense: Read error - loss of streaming
Dec 23 13:50:15 family kernel: [ 7072.494527] end_request: I/O error, dev sda, sector 1951740
Dec 23 13:50:18 family kernel: [ 7076.075259] sd 0:0:0:0: SCSI error: return code = 0x8000002
Dec 23 13:50:18 family kernel: [ 7076.075278] sda: Current: sense key: Medium Error
Dec 23 13:50:18 family kernel: [ 7076.075284]     Additional sense: Read error - loss of streaming
Dec 23 13:50:18 family kernel: [ 7076.075296] end_request: I/O error, dev sda, sector 1951732
Dec 23 13:50:19 family kernel: [ 7076.612910] UDF-fs: No partition found (1)
Dec 23 13:50:23 family kernel: [ 7080.173717] sd 0:0:0:0: SCSI error: return code = 0x8000002
Dec 23 13:50:23 family kernel: [ 7080.173736] sda: Current: sense key: Medium Error
Dec 23 13:50:23 family kernel: [ 7080.173742]     Additional sense: Read error - loss of streaming
Dec 23 13:50:23 family kernel: [ 7080.173755] end_request: I/O error, dev sda, sector 1951740
Dec 23 13:50:26 family kernel: [ 7083.721516] sd 0:0:0:0: SCSI error: return code = 0x8000002
Dec 23 13:50:26 family kernel: [ 7083.721534] sda: Current: sense key: Medium Error
Dec 23 13:50:26 family kernel: [ 7083.721540]     Additional sense: Read error - loss of streaming
Dec 23 13:50:26 family kernel: [ 7083.721553] end_request: I/O error, dev sda, sector 1951732
Dec 23 13:50:26 family kernel: [ 7084.049315] UDF-fs: No partition found (1)
Dec 23 13:50:28 family kernel: [ 7085.764214] Unable to identify CD-ROM format.
Dec 23 13:50:29 family kernel: [ 7086.776590] Unable to identify CD-ROM format.


and the device is mounted at /media/usbdisk (the device file is /dev/sda, not /dev/sda1 as you would expect, atleast as I would expect)

Hope you can help, if not any suggestions whether this is a bug with nautilus, UDEV or whatever so I can file it in an appropriate place or is it a problem with the hardware.

Thanks for your time

---

### Post by vgrisham on 2007-03-21
Bump. I'd like to know the same thing. I have an HP Photosmart 7350.

> **generice_genus said:**
> Hey I am having problems with the HP Photosmart 7450 card reader, when I insert a card it is not automatically mounted. [This thread]("http://ubuntuforums.org/showthread.php?p=1922601#post1922601") is for someone else having the same problem.

I can mount the drive after following this procedure:
1. Insert card
2. open computer:// (Places->Computer)
3. Wait for for light on card reader to stop blinking
4. Double click on "HP Photosmart 7400"
5. A dialog window will now appear saying "opening HP Photosmart 7400, wait for this to finish and
the file browser window will switch to the root directory (i.e. "/")
6. The card is now mounted at /media/usbdisk

I was hoping somebody could help me to get the card reader to work like a standard removable device (i.e. be automounted when a card is inserted) using a UDEV rule or whatever is needed. 

When a card is inserted the following is output to /var/log/messages:


After double-clicking "HP Photosmart 7400" in computer:// the following is output


and the device is mounted at /media/usbdisk (the device file is /dev/sda, not /dev/sda1 as you would expect, atleast as I would expect)

Hope you can help, if not any suggestions whether this is a bug with nautilus, UDEV or whatever so I can file it in an appropriate place or is it a problem with the hardware.

Thanks for your time

---

### Post by 11hjpphty76lkjj on 2007-03-23
Ubuntu should automount the photocards using the hotplug sub system.  This works for me all the time...

My understanding is that all usb drives/cdrom/hotswap devices are now being mounted under /media/ and not /dev/sda*.

If for some reason it's not being automounted you could use fstab to mount the device.  Lots of info on how to do that in the forums.

Hope this helps.

---

