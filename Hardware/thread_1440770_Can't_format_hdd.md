---
title: "Can't format hdd"
date: 2010-03-27
forum: Hardware
---

### Post by greatermold on 2010-03-27
I've had an old WD (4 years) external hard drive that I have merged into an internal drive.  It is a 1 TB disk and is used completely for media like movies, music, pics, etc.  It is completely separate from my boot disk.

A few weeks ago, It started acting up.  Whenever I played music, it would work for a few minutes, then completely stop.  If I left it alone, It would resume play maybe an hour later.

I moved what I could off the drive and got everything off except about 2000+ songs of 3000.

I go to use fdisk and it is completely fine.  It writes the partition.  Though, when I run 

# mkfs.ext4 /dev/sdb

it just hangs at 364/3496  (ish)

I know it sounds like my drive is dieing, but is there anything I can do to save it and return my 1TB drive to working order?

---

### Post by zeroseven0183 on 2010-03-27
Hi! I assume you have it as EXT4? or EXT3? Can you do an [fsck]("http://linux.about.com/od/commands/l/blcmdl8_fsck_.htm") to that disk?

---

### Post by jerrrys on 2010-03-27
[ATTACH]151671[/ATTACH]  testdisk?

---

### Post by psusi on 2010-03-27
mkfs /dev/sda tries to format a filesystem on the ENTIRE DISK rather than inside an individual partition, which is not what you want.  You also might want to run the SMART diganostics in system -> administration -> disk utility.

---

### Post by greatermold on 2010-03-28
The screenshot attached is what disk utilities looks like.  To me, that looks normal.  When I go to create a partition, it will hang until it errors out on me. see error is below:

Error creating file system: helper exited with exit code 1: helper failed with:
mke2fs 1.41.9 (22-Aug-2009)
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir


UPDATE: after receiving the error above, it seems like it was successfully partitioned.  This came AFTER i zero'd out the drive.  Im still messing around with it, but when i opened gparted, it recognizes the partition 'sdb1' and the mount point, but the filesystem is unknown.  -- see "screenshot2"

Looking for guidance from here?

---

### Post by psusi on 2010-03-28
You are not looking at the drive health status screen.  Go into the smart page on the drive and run the long smart selftest and look for any bad sectors.  Also did you mkfs /dev/sdb or /dev/sdb1?  If the former you trashed the partition table.

---

### Post by bear24rw on 2010-03-28
are you able to format it with gparted?

---

### Post by greatermold on 2010-04-14
sorry for the late response...
 
@bear24rw I cannot format using gparted.  When I try, it just hangs and does nothing
 
@psusi - messing around, I might have instructed the later command, but I am not sure.  If I did, is there a way to rewrite the partition table?  Or is the HDD now considered "bad"?

---

### Post by psusi on 2010-04-15
Please do as I asked before and check the drive health on the SMART screen.  If you trashed the MBR then your data is more or less lost.  If there is nothing wrong with the drive then you should just be able to repartition and start using it fresh.

---

