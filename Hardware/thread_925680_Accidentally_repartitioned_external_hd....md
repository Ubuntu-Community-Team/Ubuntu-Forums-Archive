---
title: "Accidentally repartitioned external hd..."
date: 2008-09-20
forum: Hardware
---

### Post by kaivar on 2008-09-20
I know this has nothing to do whatsoever with any operating system... it's just that I was using gnome terminal and following a tutorial on how to do a persistent install on a flash drive. Apparently, I wasn't partitioning my flash drive but my external instead.

So, just lay it down on me. If I accidentally repartitioned my external hard drive, what is the possibility of ME recovering data there? (It's like 500GB and I have basically one year of my life in there).


:( I really don't know whether to cry or to laugh at my stupidity...

---

### Post by IntuitiveNipple on 2008-09-20
If you only did partitioning you've only changed 64 bytes (the partition table) in the first sector of the drive. DON'T DO ANYTHING ELSE :)


Now... can you remember how that drive was partitioned and what file-systems were used?

What tool(s) did you use to change the partition? What is the URL of the guide you were following?

If it had a single partition that used the entire drive then recovery is as simple as recreating a default partition table.

Let us know what you can remember and let's see.

---

### Post by kaivar on 2008-09-20
Here's the page I was following. It's been only my first month on ubuntu... and this was, by far, the most stupid mistake I've ever done on either linux or M$. :lolflag:

```
http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-linux/
```

The 500GB external was a single partition on FAT32.

---

### Post by IntuitiveNipple on 2008-09-20
How far did you go in [those instructions](http://www.pendrivelinux.com/2008/05/21/usb-xubuntu-804-persistent-install-from-linux/) before realising and stopping?

---

### Post by kaivar on 2008-09-20
**12. Remove and re-insert your flash drive (if prompted that a new medium has been detected, select to open in a new window and click ok)**


This is when I removed and reinserted my flash drive... and it opened the untouched contents. I went... oops.

---

### Post by IntuitiveNipple on 2008-09-20
That's not so great - two new file-systems have been written to the two new partitions, over-writing whatever was there previously.

I asked before but you didn't answer... how many partitions and what file-systems were on the drive before this happened?

---

### Post by kaivar on 2008-09-20
I'm sorry... I did edit the post where I put the link hoping you wouldn't miss it. I'm guessing you did. Sorry about that.

I said there that it was a 500GB external with one partition on FAT32.

---

### Post by IntuitiveNipple on 2008-09-21
> **kaivar said:**
> I'm sorry... I did edit the post where I put the link hoping you wouldn't miss it. I'm guessing you did. Sorry about that.

I said there that it was a 500GB external with one partition on FAT32.
Sorry about that... I'm long overdue sleep here - eyes dead, but brain hyper!

Okay, so it will have started at sector 63 (assuming the relatively standard 63 sectors per track convention). The new first partition (750MB) starts in the same place so it is likely at least one of the FATs (File Allocation Tables) has been partially over-written.

However, the difference in sizes 500GB vs 750MB means the FAT size will be much smaller and as no files were written to the new file-system the damage might be small.

If the second FAT survived intact then the first can be recreated from it easily.

That leaves the issue of directories that had their contents over-written, and files that now have data in them from the two file-system format operations (mkfs).

On the face of it, based on these assumptions, it is possible to recover a good proportion of what is on the drive.

Do you know what percentage of the drive was used up when this happened? That'll give an indication of how far into the drive the data to be recovered extends.

Don't do this yet (unless you're brave and careful), but here's a an idea of what you might be able to do to recover files:

1. Use fdisk to recreate a single partition on the disk with FAT32 type.
2. Use [testdisk](http://www.cgsecurity.org/wiki/TestDisk) to attempt recovery of data (installed using sudo apt-get install testdisk).

I'll check in again tomorrow after I've had some sleep.

---

