---
title: "Blank Partition Table"
date: 2006-10-02
forum: Hardware &amp; Laptops
---

### Post by burnboy on 2006-10-02
I have a blank partition table and I need to know how to restore it without losing any data (i.e., without fully reformating the drive).

Here's the partition list:

```
root@atom:/# fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9351    75111876   83  Linux
/dev/sda2            9352        9726     3012187+   5  Extended
/dev/sda5            9352        9726     3012156   82  Linux swap / Solaris

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
root@atom:/#

```

Here's the current GParted screenshot
[IMG]http://burnboy.net/images/gparted.jpg[/IMG]

How I got to this point:
(Original disk was full 250 gig ext3 with a single folder called /files)
1. Opened gparted, resized drive to open last 40 gigs for 'unallocated'.
2. Rebooted, installed Vista on the remaining 40 gigs
3. Rebooted, booted into DOS using [Ultimate Boot CD]("http://www.ultimatebootcd.com/")
4. Formatted MBR with 'fdisk /mbr' (I kind of think this is where I ****** up, I did it in a hurry before leaving for work this morning because I can't even remember if that's how to clear the MBR. It didn't actually seem to help so I moved on to Step 5 as a workaround)
5. Rebooted and used UBCD to boot into the Ubuntu disk.

Now I'm seeing the fdisk and gparted above. I don't have the option of getting another HD right away and I'm hoping to be able to fix this via VNC/SSH while at work (as the drive holds my music server and..well I need my tunes, man).

I've researched dd_rescue and it seems I can rescue data but I only have the ~30 gigs of space available on the main drive and I have about 100 gigs of data I'd rather not have to lose from a working partition.

Any help is greatly appreciated.

---

