---
title: "Corrupted External USB HDD"
date: 2011-04-02
forum: Hardware
---

### Post by TEACAK on 2011-04-02
Hi All,

The other day I was using Nautilus to browse through my external disk and look at some pictures. The viewer I was using was the default, Eye of GNOME.

Anyways, I closed one image or something like that (no file deletion or anything like that) and then the file manager closed by itself. When I reopened the file manager, everything in the root directory of the drive was still there, but there is nothing in any subdirectory.

Both Nautlis and the Windows file manager say that the drive has ~200GB used, which I expect, but I get some very interesting stuff when I start ls-ing around on the disk.

```
matt@herbert:~$ ls -al /media/TOSHIBA\ EXT
total 998276
drwx------ 11 matt matt      32768 1969-12-31 18:00 .
drwxr-xr-x  4 root root       4096 2011-04-02 11:52 ..
drwx------  2 matt matt      32768 2009-10-11 08:07 autorun
-rw-r--r--  1 matt matt        120 2009-02-27 17:35 autorun.inf
-rw-r--r--  1 matt matt        137 2009-04-28 10:57 autorun.new
drwx------  0 matt matt          0 2011-03-26 10:14 Backup
drwx------  0 matt matt          0 2011-03-26 10:14 Lake-gopro
-rw-r--r--  1 matt matt      13536 2011-03-11 12:24 MATTHEW.SBW
-rw-r--r--  1 matt matt      13536 2011-03-11 12:24 MATTHEW.SBW.bak
drwx------  0 matt matt          0 2011-03-26 10:14 New Music
drwx------  0 matt matt          0 2011-04-02 11:50 $RECYCLE.BIN
drwx------  0 matt matt          0 2011-03-26 10:14 Recycled
drwx------  0 matt matt          0 2011-03-26 10:14 System Volume Information
drwx------  0 matt matt          0 2011-03-26 10:14 Work
drwx------  0 matt matt          0 2011-03-26 10:14 WPF
-rw-r--r--  1 matt matt 1022024804 2007-08-17 02:13 Zeitgeist (2006).DVDrip.bibescu.avi
```

As you can see several directories have a size of 0 (which isn't, or at least wasn't the case; they all had data in them.) Here is the output of running ls -al on one of those directories.

```
matt@herbert:~$ ls -al /media/TOSHIBA\ EXT/Backup/
total 0
```

Notice that it doesn't list self or parent directory (i.e. . or ..).

I'm pretty sure that this is some kind of file table corruption. If this is the case, what is the best way to try and get my data back? If not, does anyone have any clues as to what the problem may be?


Edit:

I've done some more research and learned a bit about fsck. So I ran fsck and here's the output.

```
matt@herbert:~$ sudo fsck -nvf /dev/sdb1
fsck from util-linux-ng 2.17.2
dosfsck 3.0.9 (31 Jan 2010)
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
Checking we can access the last sector of the filesystem
Boot sector contents:
System ID "MSWIN4.1"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
     32768 bytes per cluster
        32 reserved sectors
First FAT starts at byte 16384 (sector 32)
         2 FATs, 32 bit entries
  39066624 bytes per FAT (= 76302 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 78149632 (sector 152636)
   9765354 data clusters (319991119872 bytes)
63 sectors/track, 255 heads
      2048 hidden sectors
 625135292 sectors total
/System Volume Information
 Start does point to root directory. Deleting dir. 
/Work
 Start does point to root directory. Deleting dir. 
/Recycled
 Start does point to root directory. Deleting dir. 
/$RECYCLE.BIN
 Start does point to root directory. Deleting dir. 
/WPF
 Start does point to root directory. Deleting dir. 
/Lake-gopro
 Start does point to root directory. Deleting dir. 
/New Music
 Start does point to root directory. Deleting dir. 
/Backup
 Start does point to root directory. Deleting dir. 
Reclaiming unconnected clusters.
Unable to create unique name
```

I also found [an unresolved thread with a similar problem]("http://ubuntuforums.org/showthread.php?t=1278186"), although I am certain that the HDD was plugged in the whole time and I have never improperly disconnected it from any machine. Weird.

---

### Post by TEACAK on 2011-07-21
Just giving this thread a bump, I've been busy and haven't had much time to look at it any more, but maybe someone knows how to help me :)

---

