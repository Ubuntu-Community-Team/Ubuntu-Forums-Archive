---
title: "USB Flash Pen Drive Kingston Data Traveler 1Gb won't mount"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by tomoiaga on 2007-02-12
Hello folks,

I use a USB Flash drive Kingston, 1Gb, and it used to work very well until today when it mounted, but when I opend the folder, it hanged. I killed the File browser window, but the Flash drive was no longer mounted. It will not mount even after plug-off and plug in, or at computer restart :(

On the windows machine it mounts perfect, I copied the content, reformatted it to FAT (I think it was also FAT before), but still no result. The Ubuntu device manager recongnises it, though, as seen in [this]("http://picasaweb.google.com/vasile.tomoiaga/Ubuntu/photo#5030714048516767586") picture.

But at (manual) mount I get some nice error: 

[INDENT]vasile@YHWH:~$ sudo mount /dev/sda /mnt/usbflash
Password:
mount: you must specify the filesystem type
vasile@YHWH:~$ sudo mount -t vfat /dev/sda /mnt/usbflash
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

vasile@YHWH:~$ dmesg | tail
[17180465.188000] sda: assuming drive cache: write through
[17180465.188000]  sda: sda1
[17180465.944000] sd 1:0:0:0: Attached scsi removable disk sda
[17180465.944000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17180606.060000] cramfs: wrong magic
[17180606.864000] VFS: Can't find ext3 filesystem on dev sda.
[17180608.076000] FAT: invalid media value (0x00)
[17180608.076000] VFS: Can't find a valid FAT filesystem on dev sda.
[17180648.400000] FAT: invalid media value (0x00)
[17180648.400000] VFS: Can't find a valid FAT filesystem on dev sda.
vasile@YHWH:~$[/INDENT]

Here is the output of /var/log/messages when I plug it in:

vasile@YHWH:~$ tail -n 0 -f /var/log/messages
Feb 17 09:32:00 YHWH kernel: [17189328.384000] usb 2-2: new full speed USB device using uhci_hcd and address 3
Feb 17 09:32:03 YHWH kernel: [17189331.420000] usb 2-2: configuration #1 chosen from 1 choice
Feb 17 09:32:03 YHWH kernel: [17189331.672000] scsi1 : SCSI emulation for USB Mass Storage devices
Feb 17 09:32:09 YHWH kernel: [17189337.468000]   Vendor: Kingston  Model: DataTraveler 2.0  Rev: PMAP
Feb 17 09:32:09 YHWH kernel: [17189337.468000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Feb 17 09:32:11 YHWH kernel: [17189339.992000] SCSI device sda: 1953792 512-byte hdwr sectors (1000 MB)
Feb 17 09:32:12 YHWH kernel: [17189340.748000] sda: Write Protect is off
Feb 17 09:32:15 YHWH kernel: [17189343.768000] SCSI device sda: 1953792 512-byte hdwr sectors (1000 MB)
Feb 17 09:32:16 YHWH kernel: [17189344.524000] sda: Write Protect is off
Feb 17 09:32:16 YHWH kernel: [17189344.524000]  sda: sda1
Feb 17 09:32:16 YHWH kernel: [17189345.280000] sd 1:0:0:0: Attached scsi removable disk sda
Feb 17 09:32:16 YHWH kernel: [17189345.280000] sd 1:0:0:0: Attached scsi generic sg0 type 0

Any help ?

---

### Post by tomoiaga on 2007-02-17
Come on, nobody ? Is it possible that the drive is detected by the hotplug but not mounted ? Without error messages ?

I even try to mount it myself, but see the result:

vasile@YHWH:~$ sudo mount -t vfat /dev/sda /media/usb1
Password:
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

There is plenty of evangelism for free/open source software and OS's but even for me (being programmer) is hard to convert :(. I mean, the main reson is not that it is better, for this forum is an evidence that it gives lots of headache for users, that were not encountered when using Windows, but because of freedom.

---

### Post by yabbadabbadont on 2007-02-17
You are trying to mount the wrong device.  The one you used refers to the entire drive.  You need to use the one for the only partition on that drive: "sda: sda1"

sudo mount -t vfat /dev/sda1 /media/usbflash

Change usbflash to whatever mount point you have available in /media for your drive.

---

### Post by meng on 2007-02-17
/dev/sda is not a partition, it's the whole drive
try /dev/sda1

---

### Post by Jose Catre-Vandis on 2007-02-17
We have found these flash drives to be buggy under Windows, completely freezing the OS, especially if Word is open when inserted

---

### Post by tomoiaga on 2007-02-17
Thanks guys,

If the system recognizes the device, but is not mounted automatically, then I can mount it manually using /dev/sda1.

---

