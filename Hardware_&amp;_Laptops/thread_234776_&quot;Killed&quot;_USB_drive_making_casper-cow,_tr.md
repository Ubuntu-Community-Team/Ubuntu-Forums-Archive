---
title: "&quot;Killed&quot; USB drive making casper-cow, trying to bring it back"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by boyinthebands on 2006-08-12
Not thinking very well, I got a spiffy new 2 Gig flash drive (SanDisk Cruzer Micro) and tried to format it as casper-cow for use with a persistance LiveCD after I saw this hack in a Ubuntu hacks book. I thought that was cool but now I'm in over my head.

I've since learned (but after) that casper-rw is the right name and all the rest -- but not before doing *something* that keeps me from seeing or using the flash drive on my machine (Ubuntu 6.06), on a eMac (OS X) or a Windows XP machine. At this point, I would just like to use this flash drive to tote around photos because it feels like a tiny boat anchor now. I can't find anything in the forum or when Googling.

Here's what I did and what I see, and plead for your help and patience.

1. The commands I executed were sudo umount /dev/sda1 and sudo mkfs.ext3 -b -L casper-cow /dev/sda1 -- I did something else in a fit of Google-induced fixing.

2. I did not, however, uninstall the U3 software, but did remove them. I'm not sure that matters.

3. df -h doesn't show the usb drive, even when it is plugged in and flashing.

4. A segment of dmesg

```
[17273002.184000]   Vendor: SanDisk   Model: Cruzer Micro      Rev: 2033
[17273002.184000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17273002.188000] SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
[17273002.196000] sda: Write Protect is off
[17273002.196000] sda: Mode Sense: 02 00 00 00
[17273002.196000] sda: assuming drive cache: write through
[17273002.208000] SCSI device sda: 256000 512-byte hdwr sectors (131 MB)
[17273002.212000] sda: Write Protect is off
[17273002.212000] sda: Mode Sense: 02 00 00 00
[17273002.212000] sda: assuming drive cache: write through
[17273002.212000]  sda: sda1
[17273002.216000] sd 7:0:0:0: Attached scsi removable disk sda
[17273002.216000] sd 7:0:0:0: Attached scsi generic sg0 type 0
[17273002.220000] usb-storage: device scan complete
[17273003.732000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17273040.896000] usb 1-2: USB disconnect, address 9
[17273040.896000] sd 7:0:0:0: rejecting I/O to device being removed
[17273040.896000] Buffer I/O error on device sda1, logical block 501
[17273040.896000] lost page write due to I/O error on sda1
[17273040.896000] sd 7:0:0:0: rejecting I/O to device being removed
[17273040.896000] Buffer I/O error on device sda1, logical block 508
[17273040.896000] lost page write due to I/O error on sda1
[17273040.896000] Buffer I/O error on device sda1, logical block 509
[17273040.896000] lost page write due to I/O error on sda1
[17273045.412000] usb 1-2: new full speed USB device using uhci_hcd and address 10
[17273045.556000] scsi8 : SCSI emulation for USB Mass Storage devices
[17273045.556000] usb-storage: device found at 10
[17273045.556000] usb-storage: waiting for device to settle before scanning
[17273056.168000] usb 1-2: reset full speed USB device using uhci_hcd and address 10
[17273061.916000] usb 1-2: reset full speed USB device using uhci_hcd and address 10
[17273067.664000] usb 1-2: reset full speed USB device using uhci_hcd and address 10
[17273067.800000] usb-storage: device scan complete
```


5. There is a directory /media/casper-cow -- when I pulled it up in Nautilus -- its contents: nothing; location:/media (of course); and volume: /


Does anyone have a suggestion?

---

### Post by kievking on 2006-08-12
I had a similar experience. I have a 1G flash drive which worked fine until I added casper-rw to one of the two partitions. After I created a casper-rw label, Windows no longer detected my fat32 partition and the live CD froze everytime I used persistent mode. I tried a bunch of different fixes to no avail. I eventually had to delete and reformat both partitions. I now use a flash drive with a single partition, and it works great with casper-rw.

---

### Post by boyinthebands on 2006-08-12
*I eventually had to delete and reformat both partitions.*

Please, how did you do that? I'm stumped.

---

### Post by kievking on 2006-08-13
I used Gparted to delete both partitions. If I remember correctly, I umounted one partition and deleted it. Then I had to umount the second partition and delete that one as well. Then I disconnected the flash drive, rebooted ubuntu, reconnected the flash drive and used Gparted to create a new file system.  If that doesn't work, I think you can try WindowsXP disk management or something like it to format the flash drive. Maybe a more knowledgeable member can give you a better solution if that doesn't work.

---

### Post by boyinthebands on 2006-08-13
Thanks. I'll give it a try.

---

