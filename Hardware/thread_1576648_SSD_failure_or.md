---
title: "SSD failure or ?"
date: 2010-09-17
forum: Hardware
---

### Post by marrtys on 2010-09-17
Hi, i,ve got an asus eee pc 900 with Runcore 32 GB SSD, once i decided to upgrade from kubuntu 9.10 to 10.04, as i remember everything went fine, but after restart i,ve got black screen and read error, as the screen was cracked anyway i didnt bother to go further at a time. But now i decided to build a low power mini-itx pc, i found intel Mount Olive motherboard which has mini Pci express slot (perfectly fits my Runcore ssd), unfortunately trying to figure out what happened to my ssd i came across that it is unreadable. I found some similar posts in other forums, which suggests low level format. These are my results :


# dd if=/dev/zero of=/dev/sda1                    
dd: writing to `/dev/sda1': No space left on device
37816948+0 records in
37816947+0 records out
19362276864 bytes (19 GB) copied, 315.369 s, 61.4 MB/s


# dd if=/dev/zero of=/dev/sda1 bs=1024 count=10240
10240+0 records in
10240+0 records out
10485760 bytes (10 MB) copied, 0.106795 s, 98.2 MB/s

no errors on this one.

trying to format to Ext4 :

# tune2fs -O extents,uninit_bg,dir_index /dev/sda1
tune2fs 1.41.11 (14-Mar-2010)
tune2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Couldn't find valid filesystem superblock.

filesystem check :

# fsck /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

trying to get some performance measure:

# hdparm -tT /dev/sda1

/dev/sda1:
read() failed: Input/output error
 Timing buffered disk reads:  read() failed: Input/output error

also i cant see my drive in Gparted (no devices detected), but it is detected by bios, and i can see it in other menus, while trying to install Lucid Puppy.
Yes i am trying to do all this running Lucid Puppy 5.1 from RAM.

Any advice/help would be much appreciated.

---

### Post by marrtys on 2010-09-21
Does anyone have any ideas ?

---

