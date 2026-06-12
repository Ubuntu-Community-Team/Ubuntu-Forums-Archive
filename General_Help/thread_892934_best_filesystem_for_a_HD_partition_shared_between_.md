---
title: "best filesystem for a HD partition shared between windows and linux?"
date: 2008-08-17
forum: General Help
---

### Post by turtlepaul on 2008-08-17
I got a new laptop and want to create three partitions: one ubuntu, one vista an one big one in between. What filesystem should I format the shared one to?

---

### Post by tuxulin on 2008-08-17
how about fat32 is supported by linux.
you could do ntfs then mount it using ntfs-3g or adjusting the fstab file.


Tuxulin

---

### Post by cemeth on 2008-08-17
Best option would be using ext3.
You just have to install [http://fs-driver.org/](http://fs-driver.org/) on Windows (works with Vista, 64bit versions too), then you'll have a new drive letter for your ext3 partition(s). I've used it for a long time, also with XP 32bit, no problems at all.

The second option would be to use NTFS. Linux can mount NTFS partitions (rw). The disadvantage is that NTFS doesn't support Linux file permissions, so if you save stuff there and then copy it over the file permissions are usually not what you want them to be. You can play around with uid, gid, fmask and dmask mount options, but it'll never be as convenient as simply using an ext3 partition. If you're using Windows most of the time, though, using NTFS might be the better choice.

Avoid FAT32, it's probably the worst filesystem ever, and completely obsolete these days, except for things like USB sticks where you need to make sure that it's 100% compatible with everything.

---

### Post by az on 2008-08-17
> **turtlepaul said:**
> I got a new laptop and want to create three partitions: one ubuntu, one vista an one big one in between. What filesystem should I format the shared one to?

Avoid a shared partition and share both OSes.  Linux can read/write NTFS out of the box and Windows can read/write ext2/3 using fs-driver.  Do you really need a separate partition?

---

### Post by cybrsaylr on 2008-08-18
I've been using NTFS on my ext HDD but I mainly store music and pix files and have had no problems so far.

---

