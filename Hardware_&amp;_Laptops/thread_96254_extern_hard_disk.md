---
title: "extern hard disk"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by Vinger on 2005-11-28
Hello,

I bought an extern enclosure to store a SATA-disk.

When i want to access that disk, i do not find it on my system.
Somewhere on this forum, i read about this command "dmesg|tail"
This is the result.
> 
koen@ubuntu:~$ dmesg|tail
[4296098.422000] usb-storage: waiting for device to settle before scanning
[4296103.422000]   Vendor: Maxtor 6  Model: Y48E086E          Rev: YAR5
[4296103.422000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4296103.428000] SCSI device sda: 320173056 512-byte hdwr sectors (163929 MB)
[4296103.428000] sda: assuming drive cache: write through
[4296103.432000] SCSI device sda: 320173056 512-byte hdwr sectors (163929 MB)
[4296103.432000] sda: assuming drive cache: write through
[4296103.432000]  /dev/scsi/host1/bus0/target0/lun0:
[4296103.441000] Attached scsi disk sda at scsi1, channel 0, id 0, lun 0
[4296103.445000] usb-storage: device scan complete


What do i have to do now to mount that drive, or is it impossible?

---

### Post by Vinger on 2005-11-28
I searched a litle more, and find an USB device in "Locations-Computer"
When i tryed to open it, this was the error:

> 
**Cannot mount selected volume**
mount: I could not determine the filesystem type, and none was specified


Hope this information can help...

---

### Post by Vinger on 2005-12-05
Anyone an idea?

Maybe this disk is formatted as NTFS, but should i see it then?

Now, i don't see anything af that disk, unless with the previous command...

---

### Post by poptones on 2005-12-05
If it's a new disc there's probably no filesystem on it. Do 

sudo fdisk -l /dev/sda

and see what it reports. If it doesn't say something like 

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18363   147500766   83  Linux

Then you must run fdisk, create a new partition (n,p,1, follow defaults) and then put a filesystem on the drive (mkfs.msdos /dev/sda1) and you will then be able to automatically mount it.

---

### Post by Vinger on 2005-12-15
When i did that command, this was the result
> 
koen@ubuntu:~$ sudo fdisk -l /dev/sda
Password:
koen@ubuntu:~$ sudo fdisk -l /dev/sda
koen@ubuntu:~$


I tried the command twice, because there was no answer...
What can i do now?
I tried the disk under windows, and it started up normally...

(message completely edited because i gave the result of my USB-stick...)

---

### Post by Vinger on 2005-12-15
I installed qtparted...

I can't see my external disk there...

---

