---
title: "USB writes cause firefox to block"
date: 2008-11-03
forum: General Help
---

### Post by xphlo on 2008-11-03
I have an 8Gb usb with several partitions, but the two active for the ubuntu 8.04 install I just did are / (Reiser rw) and /home (Reiser rw). In general, I am extremely pleased with the setup. Startup is a hair slow, but 5 minutes in and I forget I am running on a usb. The only exception is firefox, and right now firefox is killing me. Any new actions I perform in firefox cause it to block for up to 10-15 seconds sometimes.

Initially, I tried tuning virtual memory....
Some of the first changes I made, were in /proc/sys/vm. 
swappiness = 0
dirty_expire_centisecs = 6000

and I also changed /sys/block/sdb/queue/scheduler = cfq (it was noop)
This decreased the latency to some degree, but it is not gone. 

Most programs initially READ a couple dozen blocks, and I never see them on dmesg again (vm.block_dump=1) unless I save a file or open another. This is actually true of Firefox, except that firefox keeps making WRITES to my home partition.

```

## This is an example of what dmesg prints out. I get this nearly
## everytime I do anything in Firefox.
[  906.670914] firefox(5997): dirtied inode 188 (cookies.sqlite-journal) on sdb2
[  906.670926] firefox(5997): dirtied inode 188 (cookies.sqlite-journal) on sdb2
[  906.671042] firefox(5997): dirtied inode 157 (cookies.sqlite) on sdb2
[  906.671048] firefox(5997): dirtied inode 157 (cookies.sqlite) on sdb2
[  909.492841] firefox(5997): dirtied inode 188 (sessionstore-1.js) on sdb2
[  909.556588] Xorg(5913): dirtied inode 9928711 (SYSV00000000) on tmpfs
[  907.706531] firefox(5997): dirtied inode 100 (places.sqlite-journal) on sdb2
[  907.706548] firefox(5997): dirtied inode 100 (places.sqlite-journal) on sdb2
[  907.706769] firefox(5997): dirtied inode 39921 (etilqs_lf2eqcTiTRSG8vn) on sdb5
[  907.706775] firefox(5997): dirtied inode 39921 (etilqs_lf2eqcTiTRSG8vn) on sdb5
[  907.708244] firefox(5997): WRITE block 2900152 on sdb2
[  907.708262] firefox(5997): WRITE block 2900248 on sdb2
[  907.708269] firefox(5997): WRITE block 2900256 on sdb2
[  907.708275] firefox(5997): WRITE block 2900264 on sdb2
[  907.708280] firefox(5997): WRITE block 2900280 on sdb2
[  907.708286] firefox(5997): WRITE block 2900288 on sdb2
[  907.708291] firefox(5997): WRITE block 2900296 on sdb2
[  907.708295] firefox(5997): WRITE block 2900384 on sdb2
[  909.984024] firefox(5997): dirtied inode 140 (places.sqlite) on sdb2
[  909.984032] firefox(5997): dirtied inode 140 (places.sqlite) on sdb2
[  909.984066] firefox(5997): WRITE block 2908232 on sdb2
[  909.984075] firefox(5997): WRITE block 2915048 on sdb2
[  909.984082] firefox(5997): WRITE block 2931672 on sdb2
[  909.984090] firefox(5997): WRITE block 2939400 on sdb2
[  909.984104] firefox(5997): WRITE block 2939528 on sdb2
[  909.984111] firefox(5997): WRITE block 2973432 on sdb2
[  909.984117] firefox(5997): WRITE block 2992328 on sdb2

```

Pdflush and syslogd are also contributing to the disk i/o. These two and firefox account for 99% of the entries in dmesg over a couple hour period. Syslog always writes to the root partition. Pdflush is half and half between root and home partitions.

Why is firefox able to make so many writes to the disk. Doesn´t linux cache a large portion of disk writes unless it has to swap them out? How can I stop these writes? Half of the writes are to session files...I dont care if session files make it to the disk or not.

I swear, firefox is the only app giving me these problems, and when you have 4 browsers open with 6 + tabs each, firefox blocking for even 2 seconds everytime I switch tabs/windows makes it harder to be productive, not to mention that a constantly working usb drains my battery faster.

I cant tell if I have firefox configured bad, if I need to mount my filesystems with different options (maybe journaling problems), or if I just need to tune my virtual memory.

I just need firefox to stop blocking. Battery conservation would be nice, but if you can get firefox to stop NOT RESPONDING, I will be most gracious.

---

### Post by kurtymckurt on 2008-11-03
Hello there friendly Ubuntu user! Two things you should try! First, I would try deleting the .mozilla folder in your home directory. Then reboot firefox. This might take care of the problem. Otherwise the problem might rely specifically with the inodes on the partition. Try using a boot disk and running fsck on the usb to fix all inode problems!

Good luck and Thanks!
Kurtymckurt

---

### Post by xphlo on 2008-11-03
Deleted ~/.mozilla , rebooted, it recreated the directory and Im right back.
reiserfsck reports no corruption.

I could be having issues with my reiser partitions(config,mount options).

But I still ask why the firefox dirty inodes are being flushed constantly. Nearly every other process I run gets cached during runtime, and they finally get flushed by mount when I shutdown.

I have tried to tweak every option I can find that alters VM and VFS behavior, Ive put them all back to default, and no matter how I configure, firefox still drags behind.

I also noticed that there is no entry at all under /proc/bus/usb. I did find some references under /proc/scsi. I dont think this is the problem, but to be sure ...
```

less /proc/scsi/scsi
...
Host: scsi2 Channel: 00 Id: 00 Lun: 00
  Vendor: SanDisk   Model: Cruzer              Rev: 8.01
  Type:   Direct-Access                        ANSI  SCSI revision: 00
...

```

```

less /proc/scsi/usb-storage/2
   Host scsi2: usb-storage
       Vendor: SanDisk
      Product: U3 Cruzer Micro
Serial Number: xxxxxxxxxxxxxxxxx
     Protocol: Transparent SCSI
    Transport: Bulk

```

I did do a command line install off of the ubuntu 8.04 alternate cd. Is there a chance I am missing optimized drivers or any other packages that might influence USB behavior.

---

