---
title: "HELP!  Linux cannot read hdb3!"
date: 2006-01-18
forum: Hardware &amp; Laptops
---

### Post by heftigrat on 2006-01-18
If anyone can help I would greatly appreciate it.  I have LOTS of data on hdb3 that I don't want to lose.  So here's the story:

Had Ubuntu 5.10 Breezy installed on this HDD, which is now hdb.  The "/" partition was the third on the disk.  I recently installed a new HDD w/Breezy as well, which is now hda and everything was working fine for a while, and I was still able to mount hdb3's "/".  Just today I rebooted and got a strange error (see below).  The other partitions "/boot" and "/var" are still fine.

Of course I want to retrieve the data any way possible.  Does anyone know of any method that will work, e.g. repairing the partition, reading raw data from the partition, etc.?  :confused: 

# cat /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro,usrquota,grpquota 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hdb1       /media/hdb1     ext3    defaults        0       2
/dev/hdb3       /media/hdb3     ext3    defaults        0       2
/dev/hdb4       /media/hdb4     ext3    defaults        0       2
/dev/hdd1       /media/hdd1     ext3    defaults        0       2
/dev/hda4       /var            ext3    defaults,usrquota,grpquota        0       2
/dev/hda2       none            swap    sw              0       0
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

# mount -a:
```
mount: wrong fs type, bad option, bad superblock on /dev/hdb3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

# dmesg | tail:
```
[4301529.981000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4301530.076000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4301530.076000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4301530.148000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4301530.148000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4301575.505000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[4301575.505000] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=2056322, sector=2056322
[4301575.505000] ide: failed opcode was: unknown
[4301575.505000] end_request: I/O error, dev hdb, sector 2056322
[4301575.505000] EXT3-fs: unable to read superblock
```

# grep hdb3 /var/log/*:
```
/var/log/dmesg:[4296743.344000] Buffer I/O error on device hdb3, logical block 19
/var/log/dmesg:[4296748.609000] Buffer I/O error on device hdb3, logical block 20
/var/log/dmesg:[4296753.857000] Buffer I/O error on device hdb3, logical block 21
/var/log/dmesg:[4296759.114000] Buffer I/O error on device hdb3, logical block 22
/var/log/dmesg:[4296764.379000] Buffer I/O error on device hdb3, logical block 23
/var/log/dmesg:[4296769.619000] Buffer I/O error on device hdb3, logical block 24
/var/log/dmesg:[4296774.843000] Buffer I/O error on device hdb3, logical block 25
/var/log/dmesg:[4296780.141000] Buffer I/O error on device hdb3, logical block 26
/var/log/dmesg:[4296785.422000] Buffer I/O error on device hdb3, logical block 27
/var/log/dmesg:[4296790.687000] Buffer I/O error on device hdb3, logical block 28
/var/log/dmesg:[4296795.952000] Buffer I/O error on device hdb3, logical block 29
/var/log/dmesg:[4296801.234000] Buffer I/O error on device hdb3, logical block 30
/var/log/dmesg:[4296806.532000] Buffer I/O error on device hdb3, logical block 31
/var/log/dmesg:[4296811.797000] Buffer I/O error on device hdb3, logical block 32
/var/log/dmesg:[4296817.037000] Buffer I/O error on device hdb3, logical block 33
/var/log/dmesg:[4296822.319000] Buffer I/O error on device hdb3, logical block 34
/var/log/dmesg:[4296827.600000] Buffer I/O error on device hdb3, logical block 35
/var/log/dmesg:[4296832.874000] Buffer I/O error on device hdb3, logical block 36
/var/log/dmesg:[4296838.164000] Buffer I/O error on device hdb3, logical block 37
/var/log/dmesg:[4296843.412000] Buffer I/O error on device hdb3, logical block 38
/var/log/dmesg:[4296848.669000] Buffer I/O error on device hdb3, logical block 39
/var/log/dmesg:[4296853.934000] Buffer I/O error on device hdb3, logical block 40
/var/log/dmesg:[4296859.224000] Buffer I/O error on device hdb3, logical block 41
/var/log/dmesg:[4296864.464000] Buffer I/O error on device hdb3, logical block 42
/var/log/dmesg:[4296869.687000] Buffer I/O error on device hdb3, logical block 43
/var/log/dmesg:[4296874.977000] Buffer I/O error on device hdb3, logical block 44
/var/log/dmesg:[4296880.217000] Buffer I/O error on device hdb3, logical block 45
/var/log/dmesg:[4296885.466000] Buffer I/O error on device hdb3, logical block 46
/var/log/dmesg:[4296890.747000] Buffer I/O error on device hdb3, logical block 47
/var/log/dmesg:[4296896.037000] Buffer I/O error on device hdb3, logical block 0
/var/log/dmesg:[4296901.352000] Buffer I/O error on device hdb3, logical block 1
/var/log/dmesg:[4296906.625000] Buffer I/O error on device hdb3, logical block 2
/var/log/dmesg:[4296911.932000] Buffer I/O error on device hdb3, logical block 3
/var/log/dmesg:[4296917.197000] Buffer I/O error on device hdb3, logical block 4
/var/log/dmesg:[4296922.428000] Buffer I/O error on device hdb3, logical block 5
/var/log/dmesg:[4296927.702000] Buffer I/O error on device hdb3, logical block 6
/var/log/dmesg:[4296932.942000] Buffer I/O error on device hdb3, logical block 7
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296748.609000] Buffer I/O error on device hdb3, logical block 20
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296753.857000] Buffer I/O error on device hdb3, logical block 21
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296759.114000] Buffer I/O error on device hdb3, logical block 22
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296764.379000] Buffer I/O error on device hdb3, logical block 23
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296769.619000] Buffer I/O error on device hdb3, logical block 24
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296774.843000] Buffer I/O error on device hdb3, logical block 25
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296780.141000] Buffer I/O error on device hdb3, logical block 26
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296785.422000] Buffer I/O error on device hdb3, logical block 27
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296790.687000] Buffer I/O error on device hdb3, logical block 28
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296795.952000] Buffer I/O error on device hdb3, logical block 29
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296801.234000] Buffer I/O error on device hdb3, logical block 30
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296806.532000] Buffer I/O error on device hdb3, logical block 31
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296811.797000] Buffer I/O error on device hdb3, logical block 32
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296817.037000] Buffer I/O error on device hdb3, logical block 33
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296822.319000] Buffer I/O error on device hdb3, logical block 34
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296827.600000] Buffer I/O error on device hdb3, logical block 35
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296832.874000] Buffer I/O error on device hdb3, logical block 36
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296838.164000] Buffer I/O error on device hdb3, logical block 37
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296843.412000] Buffer I/O error on device hdb3, logical block 38
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296848.669000] Buffer I/O error on device hdb3, logical block 39
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296853.934000] Buffer I/O error on device hdb3, logical block 40
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296859.224000] Buffer I/O error on device hdb3, logical block 41
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296864.464000] Buffer I/O error on device hdb3, logical block 42
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296869.687000] Buffer I/O error on device hdb3, logical block 43
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296874.977000] Buffer I/O error on device hdb3, logical block 44
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296880.217000] Buffer I/O error on device hdb3, logical block 45
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296885.466000] Buffer I/O error on device hdb3, logical block 46
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296890.747000] Buffer I/O error on device hdb3, logical block 47
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296896.037000] Buffer I/O error on device hdb3, logical block 0
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296901.352000] Buffer I/O error on device hdb3, logical block 1
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296906.625000] Buffer I/O error on device hdb3, logical block 2
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296911.932000] Buffer I/O error on device hdb3, logical block 3
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296917.197000] Buffer I/O error on device hdb3, logical block 4
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296922.428000] Buffer I/O error on device hdb3, logical block 5
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296927.702000] Buffer I/O error on device hdb3, logical block 6
/var/log/kern.log:Jan 18 17:27:17 bismarck kernel: [4296932.942000] Buffer I/O error on device hdb3, logical block 7
/var/log/kern.log.0:Jan 13 20:26:29 bismarck kernel: [4294705.282000] EXT3 FS on hdb3, internal journal
/var/log/kern.log.0:Jan 14 14:50:20 bismarck kernel: [4294693.982000] EXT3 FS on hdb3, internal journal
/var/log/kern.log.0:Jan 14 22:44:29 bismarck kernel: [4294692.089000] EXT3 FS on hdb3, internal journal
/var/log/messages.0:Jan 13 20:26:29 bismarck kernel: [4294705.282000] EXT3 FS on hdb3, internal journal
/var/log/messages.0:Jan 14 14:50:20 bismarck kernel: [4294693.982000] EXT3 FS on hdb3, internal journal
/var/log/messages.0:Jan 14 22:44:29 bismarck kernel: [4294692.089000] EXT3 FS on hdb3, internal journal
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296748.609000] Buffer I/O error on device hdb3, logical block 20
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296753.857000] Buffer I/O error on device hdb3, logical block 21
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296759.114000] Buffer I/O error on device hdb3, logical block 22
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296764.379000] Buffer I/O error on device hdb3, logical block 23
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296769.619000] Buffer I/O error on device hdb3, logical block 24
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296774.843000] Buffer I/O error on device hdb3, logical block 25
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296780.141000] Buffer I/O error on device hdb3, logical block 26
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296785.422000] Buffer I/O error on device hdb3, logical block 27
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296790.687000] Buffer I/O error on device hdb3, logical block 28
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296795.952000] Buffer I/O error on device hdb3, logical block 29
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296801.234000] Buffer I/O error on device hdb3, logical block 30
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296806.532000] Buffer I/O error on device hdb3, logical block 31
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296811.797000] Buffer I/O error on device hdb3, logical block 32
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296817.037000] Buffer I/O error on device hdb3, logical block 33
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296822.319000] Buffer I/O error on device hdb3, logical block 34
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296827.600000] Buffer I/O error on device hdb3, logical block 35
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296832.874000] Buffer I/O error on device hdb3, logical block 36
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296838.164000] Buffer I/O error on device hdb3, logical block 37
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296843.412000] Buffer I/O error on device hdb3, logical block 38
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296848.669000] Buffer I/O error on device hdb3, logical block 39
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296853.934000] Buffer I/O error on device hdb3, logical block 40
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296859.224000] Buffer I/O error on device hdb3, logical block 41
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296864.464000] Buffer I/O error on device hdb3, logical block 42
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296869.687000] Buffer I/O error on device hdb3, logical block 43
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296874.977000] Buffer I/O error on device hdb3, logical block 44
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296880.217000] Buffer I/O error on device hdb3, logical block 45
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296885.466000] Buffer I/O error on device hdb3, logical block 46
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296890.747000] Buffer I/O error on device hdb3, logical block 47
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296896.037000] Buffer I/O error on device hdb3, logical block 0
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296901.352000] Buffer I/O error on device hdb3, logical block 1
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296906.625000] Buffer I/O error on device hdb3, logical block 2
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296911.932000] Buffer I/O error on device hdb3, logical block 3
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296917.197000] Buffer I/O error on device hdb3, logical block 4
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296922.428000] Buffer I/O error on device hdb3, logical block 5
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296927.702000] Buffer I/O error on device hdb3, logical block 6
/var/log/syslog:Jan 18 17:27:17 bismarck kernel: [4296932.942000] Buffer I/O error on device hdb3, logical block 7
```

Thanks to anyone who takes the time to reply to this!  :)

---

### Post by aysiu on 2006-01-18
The easiest way to do this:

[Download a Knoppix CD](http://mirror.cs.wisc.edu/pub/mirrors/linux/knoppix/KNOPPIX_V4.0.2CD-2005-09-23-EN.iso), burn it, boot from it, click on /dev/hdb3

---

### Post by jasmuz on 2006-01-19
Smells like an inminent hard drive failure to me.

---

### Post by heftigrat on 2006-01-19
[QUOTE=jasmuz]Smells like an inminent hard drive failure to me.[/QUOTE]
That's what I was thinking, but hoping against.  Aren't there companies you can pay hundreds of dollars to that can get data off any drive, so long as the platters aren't physically damaged?  I've heard rumors.  If so, I wanna find out what methods they use!

Thanks for the input.  :)

---

### Post by heftigrat on 2006-01-19
[QUOTE=aysiu]The easiest way to do this:

[Download a Knoppix CD](http://mirror.cs.wisc.edu/pub/mirrors/linux/knoppix/KNOPPIX_V4.0.2CD-2005-09-23-EN.iso), burn it, boot from it, click on /dev/hdb3[/QUOTE]
3% downloaded so far.  ;)

---

### Post by vruum on 2006-01-19
well, if you can read the from the other partitions on the drive, it might just be a filesystem problem, have you checked the file system?
```
 sudo fsck -f /dev/hdb3 
```

---

### Post by heftigrat on 2006-01-19
[QUOTE=vruum]well, if you can read the from the other partitions on the drive, it might just be a filesystem problem, have you checked the file system?
```
 sudo fsck -f /dev/hdb3 
```[/QUOTE]
```
# fsck -f /dev/hdb3
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/hdb3
Could this be a zero-length partition?
```
Thanks for the suggestion.  It does look like the partition is completely jacked, but I have no idea why it would be.  Could two roaring Thermaltake A2016 Smart Case Fans capable of 4800 RPM placed directly in front of the HDD cage potentially cause a problem like that?

---

### Post by vruum on 2006-01-19
just to be sure. this is not an extended partition right? There are several different diagnostics you could try, for example
```
 sudo sfdisk -V /dev/hdb 
```
also, if you know who made the drive, they probably have some kind of tool available to check if the drive is about to croak, otherwise, I don't know, knoppix still might be usefull

---

### Post by heftigrat on 2006-01-19
[QUOTE=vruum]just to be sure. this is not an extended partition right?[/QUOTE]
Not sure.  I used the manual formatting/partitioning tool when I installed Ubuntu.  There are only 4 partitions (/boot, /swap, /, and /var), so I don't believe the MBR required an extended partition, but I could be wrong.  The "/" partition is ext3, which is standard but is [technically an "extended" partition]("http://en.wikipedia.org/wiki/Ext3").
[QUOTE=vruum]There are several different diagnostics you could try, for example
```
 sudo sfdisk -V /dev/hdb 
```[/QUOTE]
# sfdisk -V /dev/hdb:
```
Warning: partition 1 does not end at a cylinder boundary
```
[QUOTE=vruum]also, if you know who made the drive, they probably have some kind of tool available to check if the drive is about to croak, otherwise, I don't know, knoppix still might be usefull[/QUOTE]
IBM.  I'll try their [Drive Fitness Test]("http://www.hgst.com/hdd/support/download.htm") when I get home.  I'll also try Knoppix.  Thanks!

---

### Post by heftigrat on 2006-01-20
It's official, my drive is fuxored.  The IBM/Hitachi Drive Fitness Test gives the following error when I run the Sector Repair utility:
```
Failure Code:  0x70 - Defective Device
Technical Result Code:  70000DBD
```
If there are any hardware gurus here who know the answer to my questions below I would be grateful to hear what you have to say.
[LIST]
[*]Is there ANY way to read the raw data from the disk, ignoring the corrupted sectors?
[*]Have you heard of case fans generating enough of a magnetic field to corrupt drive sectors?
[/LIST]
I guess that's it for questions.  I am going to contact Hitachi as well and ask them the same questions.  I will post again if I find out anything of consequence.  Thank you all who have given input so far!

---

### Post by justinkempton on 2006-01-26
Hello,

I have an almost identical problem with my second hard drive /dev/hdb. However, I ran Hitachi's Drive Fitness test in quick and advanced mode and it found no problems. :) Hopefully, my problem has something to do with the partition? Here are some stats.

this is the hard disk here :
```
fdisk -l
...
Disk /dev/hdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7297    58613121    5  Extended
```

this is what my /etc/fstab looks like
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   iso9660 ro,user,noauto  0       0
/dev/sda1       /media/usb0     vfat    rw,user,auto    0       0
/dev/hdb1       /media/hd2a     auto    rw,user,auto    0       0
```

when I try a simple mount, my usb0 loads up great, but my HDb1 does not. here is the error :

```

# mount -a
mount: you must specify the filesystem type

# mount -t ext3 /dev/hdb1 /media/hd2a
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

# mount -t ext2 /dev/hdb1 /media/hd2a
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

# dmesg | tail

ACPI: Sleep Button (CM) [SLPB]
eth0: no IPv6 routers present
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
apm: overridden by ACPI.
attempt to access beyond end of device
hdb1: rw=0, want=4, limit=2
EXT3-fs: unable to read superblock
attempt to access beyond end of device
hdb1: rw=0, want=4, limit=2
EXT2-fs: unable to read superblock


```

so I tried looking at it with other means :

```
# fsck -f /dev/hdb1
fsck 1.37 (21-Mar-2005)
e2fsck 1.37 (21-Mar-2005)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/hdb1
Could this be a zero-length partition?

# sfdisk -V /dev/hdb
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

sfdisk: ERROR: sector 63 does not have an msdos signature
Warning: partition 1 does not end at a cylinder boundary


```

So, I'm at a loss, which isn't surprising since I'm new to Linux. Does anybody have any further suggestions? 

On a side note the drive is 3 or more years old, and was just installed into my Linux box 1 week ago. Originally it was formatted for windows, so I re-formatted with fdisk using the default linux format. Is that ext3?  I remember restarting, several times, and it showing up and seeing it before. It was working well before, and I was using it exclusively for a website design project. All of my files are on this drive, (2 weeks of work) plus 15 Gigs of drum loops, and countless hours of bittorrent derived video. ehh. 

I guess the worst case senario is to start over from scratch on the project, and call it good. But I do wish there was an easy GUI type interface that could smile at me first, and let me know for sure I'm screwed! :)

---

### Post by jamiedean on 2006-08-20
Hi,

If you have access to a computer running windows (yes swearing in a forum!), there is a brilliant program made by Stellar Phoenix that will do data recovery on a shafted HDD there is a version which works on Linux filesystems as i had some very important accounts data on a hdd which was also dying and it got the whole lot back after leaving it to run for many hours.

---

