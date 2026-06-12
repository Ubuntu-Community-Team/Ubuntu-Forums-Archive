---
title: "sda &amp; sdb partition devices no longer created in /dev"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by nocwage on 2008-03-25
Ubuntu 7.04
promise sata 'raid' card (tx2300)

Since November I've been using mdadm to run a RAID-1 mirror of two 500 gig drives.
I set it up using 3 partitions to create 3 mirrors.. sd[a,b]1 sd[a,b]2 sd[a,b]3
On sunday we lost power for a split second and now when Ubuntu boots it detects sda and sdb but it does not create the /dev/sda1, /dev/sdb1, /dev/sda2 etc.. files.  

fdisk -l /dev/sda SHOWS the partitions..

root@finn:~# fdisk -l /dev/sda

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1217     9775521   83  Linux
/dev/sda2            1218        3650    19543072+  83  Linux
/dev/sda3            3651       60801   459065407+  83  Linux

dmesg looks like everything is okay:

root@finn:~# dmesg |grep sda
[   30.217002] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[   30.217028] sda: Write Protect is off
[   30.217032] sda: Mode Sense: 00 3a 00 00
[   30.217055] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.217149] SCSI device sda: 976773168 512-byte hdwr sectors (500108 MB)
[   30.217163] sda: Write Protect is off
[   30.217166] sda: Mode Sense: 00 3a 00 00
[   30.217187] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[COLOR="Red"][   30.217192]  sda: sda1 sda2 sda3[/COLOR]
[   30.235974] sd 0:0:0:0: Attached scsi disk sda
[   31.230490] md: bind<sda>

but there are no sda1 etc files in /dev
root@finn:/dev# ls -la sd*
brw-rw---- 1 root disk 8,  0 2008-03-25 08:50 sda
brw-rw---- 1 root disk 8, 16 2008-03-25 08:50 sdb
root@finn:/dev#


And if I boot the system with a knoppix disk it correctly shows sda1 sdb1 sda2 etc..

I've tried running MAKEDEV sda  and MAKEDEV sdb but neither one creates the missing files..
I also tried udevtrigger and using mknod,   udevtrigger didn't seem to create anything and with my manually created devices  it complains that they aren't real block devices.. 'mknod /dev/sda1 b 8 1'

I'm positive all my data is safe but I can't ACCESS any of it until Ubuntu decides it wants to see those partitions in /dev..

What else can I try?

root@finn:/dev# lsmod |grep promise
sata_promise           13316  1
libata                125848  2 ata_generic,sata_promise
root@finn:/dev# lsmod |grep scsi
scsi_mod              142220  3 sg,sd_mod,libata

md seems to be just trying to make sda and sdb one mirror but that's not how it's supposed to be setup so I can't access the data on the 'array' it's creating as md0..

---

### Post by nocwage on 2008-03-25
I ran testdisk and it shows everything is fine with the partition table on /dev/sda and /dev/sdb
So it's just Ubuntu which is not creating the device nodes for the partitions..

Any ideas??

---

### Post by nocwage on 2008-03-25
SOLVED!

For anyone else that has had this happen I'll explain what I did.

Apparently for some unknown reason the way md worked at bootup changed.  I don't know if it had something to do with the power loss I suffered or what but for SOME reason it suddenly decided that rather than a RAID-1 based on the partitions it should be a RAID based on the FULL drives.

I kept looking at my dmesg where it kept saying that sda and sdb were being talked to by md so I decided I would modify my initramfs and remove the startup script for mdadm so that it WOULD NOT load at the initial boot.

I did this by going into /usr/share/initramfs-tools/scripts/local-top and moving the 'mdadm' script into my home directory.
I then rebuilt my init by running 'update-initramfs -u'
I rebooted and BEHOLD I suddenly had sda1, sda2, sda3, sdb1,sdb2,sdb3

---

