---
title: "Suddenly cannot mount NTFS external hard drive"
date: 2011-01-03
forum: Hardware
---

### Post by dragoon3 on 2011-01-03
Hello all, I wonder if you could help me out. I'm not a very knowledgeable user so it would be appreciated if any help could be kept simple. 

So I have a Hitachi 1TB external hard drive. I don't have it plugged in all the time, and when I need it, I mount it by

```
[CODE]sudo mount /external
```[/CODE]

But now I get an error mesage:

```
ntfs-3g: Failed to access volume 'UUID=9218E01B18DFFBDB': No such file or directory

ntfs-3g 2010.8.8 external FUSE 28 - Third Generation NTFS Driver
		Configuration type 1, XATTRS are on, POSIX ACLS are off

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2010 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  http://ntfs-3g.org

```

I dual-boot with Windows, but I cant access it there either.

Any ideas?

---

### Post by wyliecoyoteuk on 2011-01-03
If you can't access it from windows either, it may be faulty or corrupted.
Have you tried the disk utility in system>administration menu?
Can you see the drive in there?
Are there any partitions visible?

If yes to the first and no to the second, the disk partition table may be corrupt.
This can often be recovered.

---

### Post by coffeecat on 2011-01-03
A couple of comments.

> **dragoon3 said:**
> So I have a Hitachi 1TB external hard drive. I don't have it plugged in all the time, and when I need it, I mount it by

```
sudo mount /external
```

Why? External NTFS driver are automounted by the system when you plug them in. Was this one not automounted?

> **dragoon3 said:**
> But now I get an error mesage:

```
ntfs-3g: Failed to access volume 'UUID=9218E01B18DFFBDB': No such file or directory
```....

I dual-boot with Windows, but I cant access it there either.



That doesn't sound good.

Plug the drive in, switch it on but don't try your mount command. Instead, run these two commands from the terminal:

```
sudo fdisk -lu
dmesg | tail
```Post the two outputs. That may tell us something.

---

### Post by dragoon3 on 2011-01-03
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7b5e4268

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    15448063     7723008   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *    15448064   230309392   107430664+   7  HPFS/NTFS
/dev/sda3       230323905   390716864    80196480    5  Extended
/dev/sda5       230323968   335774564    52725298+   b  W95 FAT32
/dev/sda6       335774628   374844644    19535008+  83  Linux
/dev/sda7       374844708   384612164     4883728+  83  Linux
/dev/sda8       384612228   390716864     3052318+  82  Linux swap / Solaris

Disk /dev/mspblk0: 63 MB, 63700992 bytes
8 heads, 16 sectors/track, 972 cylinders, total 124416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mspblk0p1   *          39      124415       62188+   1  FAT12
kai@kai-laptop:~$ dmesg | tail
[   74.948690] wlan0: authenticate with 00:18:4d:5d:34:f8 (try 1)
[   74.949312] wlan0: authenticated
[   74.949345] wlan0: associate with 00:18:4d:5d:34:f8 (try 1)
[   74.953710] wlan0: RX AssocResp from 00:18:4d:5d:34:f8 (capab=0x431 status=0 aid=2)
[   74.953716] wlan0: associated
[   75.060324] audit_printk_skb: 3 callbacks suppressed
[   75.060329] type=1400 audit(1294050982.911:16): apparmor="DENIED" operation="open" parent=1643 profile="/sbin/dhclient3" name="/var/lib/wicd/dhclient.conf" pid=1900 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   79.777035] wlan0: no IPv6 routers present
[  149.255683] lo: Disabled Privacy Extensions
[  285.614559] lo: Disabled Privacy Extensions
```

wyliecoyoteuk: It doesn't show up on the list.
coffeecat: It didn't automount.

---

### Post by coffeecat on 2011-01-03
Neither fdisk nor dmesg show any sign of the system recognising the Hitachi drive. This indicates a hardware problem rather than just a filesystem corruption. Taking things in turn, the problem could be the drive power supply, the drive enclosure, or the hard drive itself, or the computer USB interface.

Take the last one first. Do other USB devices work on the computer USB interface that you were using?

USB brick power supplies do fail occasionally. Are you getting a light on the enclosure? Even if you are, the power supply could be failing, delivering inadequate voltage. If you have a compatible one, try an alternative power supply.

Next thing is to remove the HD from the enclosure. Do you have another enclosure you could try it in? If not, as it's probably a SATA drive, and if you have a desktop machine rather than a laptop, try connecting the bare drive to the motherboard. Or if you have an eSATA connector you could try that.

Lastly, for completion, if you have another usable SATA drive, you could put that into the enclosure to see if the enclosure itself is working.

---

### Post by dragoon3 on 2011-01-03
Thanks for your help, but it suddenly started to work. 

I plugged it into another XP machine and it loaded up as normal. I then retried mounting on Ubuntu and things were fine. Now if you's excuse me, I'm going to go and back everything up.

---

