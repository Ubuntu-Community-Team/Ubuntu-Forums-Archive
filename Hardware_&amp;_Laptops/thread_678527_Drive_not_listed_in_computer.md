---
title: "Drive not listed in computer:///"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by Deiz on 2008-01-26
I have four hard drives - Two ext3 and two NTFS. The two NTFS drives are older Windows drives. They both mount fine - Both manually (via Nautilus) and automatically (via fstab.)

The first ext3 drive is my Ubuntu drive - It obviously works fine. The second, however, is an empty ext3 partition that was formerly an unused NTFS storage drive that I formatted to ext3 for convenience.

The drive is mountable through GParted without issue, and fstab can do it automatically. It doesn't show up in Nautilus, however, when viewing computer:/// whether it's mounted or not.

I can access its mount point without issue (/media/disk) and running mount -a doesn't produce any errors.

Here's a sample from my fstab file:

/dev/sdb1 /media/disk ext3 defaults 0 0
/dev/sdc1 /media/disk-1 ntfs defaults.rw 0 0
/dev/sdd1 /media/disk-2 ntfs defaults.rw 0 0

An interesting quirk is that when I blank the drive, it shows up in computer:///, but as soon as GParted begins to format it to anything, it disappears - I've tried ReiserFS, Ext3, Ext2, thusfar.

---

### Post by rosegarden78 on 2008-01-26
Wowzers!  I thought everything shows up under /etc/fstab or /etc/mtab? Good luck!

---

