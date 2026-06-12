---
title: "USB mass storage issue"
date: 2007-03-22
forum: Hardware &amp; Laptops
---

### Post by davidhdez on 2007-03-22
Hi,

As many others I've been experiencing difficulties with my USB mass storage device. I tried to find a solution in some other threads but (as some others) it didn't quite solved my situation.

I use edgy eft. In the past I didn't use to have a problem with Edgy Eft to automatically recognize the drive. But a couple of weeks ago I reinstalled the whole system and when I plug my USB drive the system simply does NOTHING!

I tried my brother's USB drive (a Kingstone) and it actually worked fine, I don't know why mine isn't working.

I use Kubuntu and when I check the 'Disk & Filesystems' I can actually see my USB drive under the 'name' column. However, the rest of the columns are empty: Mount Point, Type, Device and Enabled.

The 'etc/fstab' looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=f8f54ee9-b184-4ceb-a46d-8ca2d5452117 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda5
UUID=9b5acb04-53de-4bd2-843b-cb01b9a18a92 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/ /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0
```

The relevant part of the output of the "david@david-desktop:~$ dmesg" command is:

```
[17179594.856000] usb-storage: device scan complete
[17179594.896000]   Vendor: CREATIVE  Model: Zen Vision:M      Rev: 0001
[17179594.896000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17179594.920000] SCSI device sda: 16777216 512-byte hdwr sectors (8590 MB)
[17179594.920000] sda: Write Protect is off
[17179594.920000] sda: Mode Sense: 00 0b 08 00
[17179594.920000] sda: assuming drive cache: write through
[17179594.924000] SCSI device sda: 16777216 512-byte hdwr sectors (8590 MB)
[17179594.924000] sda: Write Protect is off
[17179594.924000] sda: Mode Sense: 00 0b 08 00
[17179594.924000] sda: assuming drive cache: write through
[17179594.924000]  sda:<6>ACPI: Power Button (FF) [PWRF]
[17179596.248000] ACPI: Power Button (CM) [PWRB]
[17179596.248000] ACPI: Sleep Button (CM) [SLPB]
[17179596.364000] ibm_acpi: ec object not found
[17179596.400000] pcc_acpi: loading...
[17179597.652000]  unknown partition table
[17179597.656000] sd 0:0:0:0: Attached scsi removable disk sda
[17179597.684000] sd 0:0:0:0: Attached scsi generic sg0 type 0
```

I also ran the lsusb command:

```
david@david-desktop:~$ lsusb
Bus 004 Device 003: ID 041e:4133 Creative Technology, Ltd
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 045e:0009 Microsoft Corp. IntelliMouse
Bus 001 Device 001: ID 0000:0000
```

By the way, I plugged my USB device to a Windows XP computer and it had no problem whatsoever.

I really hope I'm not repeating someone else's post and moreover, I hope someone can help me with this problem. What I want is to plug in my USB drive and being able to read/see/use it as normal.

Many thanks,
David

---

### Post by taurus on 2007-03-22
What's the output of this command from a terminal after you plug in your USB drive?

```
sudo fdisk -l
```

---

### Post by davidhdez on 2007-03-22
Hi Taurus,

The output for the command is:

```
david@david-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9545    76670181   83  Linux
/dev/hda2            9546        9732     1502077+   5  Extended
/dev/hda5            9546        9732     1502046   82  Linux swap / Solaris

Disk /dev/sda: 8589 MB, 8589934592 bytes
64 heads, 32 sectors/track, 8192 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      912975      995343    84344761   69  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?      830821     1743849   934940732+  73  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?           2           2           0   74  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sda4         1409025     1409050       26207+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

---

### Post by taurus on 2007-03-22
Maybe you want to connect that USB drive to a Windows machine and defrag it.  Then, plug it back to your Ubuntu and see if the kernel see any partition table on that thing now.

```
sudo fdisk -l
```

---

### Post by davidhdez on 2007-03-22
Thanks Taurus,

I'll do that. I only need to wait for my brother to come back home and do it in his computer.

I'll let you know (post) what happens.

Cheers,
David

---

### Post by davidhdez on 2007-03-23
Excellent.......Problem solved, I formated the USB drive and Kubuntu read it without a problem.

Many thanks

---

