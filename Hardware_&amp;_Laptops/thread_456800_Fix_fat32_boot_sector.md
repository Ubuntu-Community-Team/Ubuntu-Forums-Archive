---
title: "Fix fat32 boot sector"
date: 2007-05-28
forum: Hardware &amp; Laptops
---

### Post by ge0ffrey on 2007-05-28
Hi,

I have an external hard drive formatted as a single fat32 partition with more data on it then I can store on my small pc hard drive at the moment.
It got corrupted by a friend of mine, working on windows.

If he or I plug it in in windows, windows slows down horribly, the disk get accessed a lot, but nothing happens. Windows file browser doesn't even want to start up.
If I plug it in in Ubuntu, everything works perfect (1-0 for ubuntu I 'd say :))

I tried gparted to fix it, but it just says there's an error on it, so it won't let me do anything.
I trie fshk (or whatever it is called) from the command line.
It said the boot sector file "original" was different from "backup", and asked me what to do, I said "put backup over original", it also located a bug at sector or something like "12345 of 23456".

How can I fix my fat32 external hard drive?
Thanks for any help in advance.

PS: They say NTFS corrupts less (of course, ext3 would be a lot better, but I can't force my friends to use linux or even a ext3 driver on windows...), so is it possible to convert a fat32 to ntfs without loosing the data?

---

### Post by ramjet_1953 on 2007-05-28
You could try downloading SpinRite

[http://www.grc.com/spinrite.htm](http://www.grc.com/spinrite.htm)

There is a demo available.

You just run the executable in Windows, or under Wine in Linux, to create the iso.

Then just burn the iso image to disk (remember to burn it as an iso, not a data disk) at a slow speed, no greater than 4 X.

You then boot from the CD and it allows you to recover lost data and damaged sectors, in many cases, but not all.

Unfortunately, it is not free, but is not that expensive.

Regards,
Roger :cool:

---

### Post by ge0ffrey on 2007-05-28
fsck says there's a problem, but whatever options I try, it refuses to fix them and always gives this output:

```
[/sbin/fsck.vfat (1) -- /dev/sdb1] fsck.vfat -r -v /dev/sdb1
dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Checking we can access the last sector of the filesystem
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:03/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 2
Boot sector contents:
System ID "MSWIN4.1"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
     32768 bytes per cluster
        32 reserved sectors
First FAT starts at byte 16384 (sector 32)
         2 FATs, 32 bit entries
  39062016 bytes per FAT (= 76293 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 78140416 (sector 152618)
   9765385 data clusters (319992135680 bytes)
63 sectors/track, 255 heads
        63 hidden sectors
 625137282 sectors total
Got 36175872 bytes instead of 39061548 at 16384
```

---

### Post by ge0ffrey on 2007-05-28
ok, if anyone else has this problem

1) make sure your root (sudo su)
2) make sure to add -w:
fsck -rw -v -V /dev/sdb1

---

