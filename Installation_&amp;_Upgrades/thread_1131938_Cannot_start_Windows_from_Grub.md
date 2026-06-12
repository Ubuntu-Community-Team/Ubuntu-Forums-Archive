---
title: "Cannot start Windows from Grub"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by kapshoo on 2009-04-21
I have 2 SATA drives with Ubuntu 8.10 on SATA1 and Windows XP Pro on SATA2.

This is how my disks look like:
Disk /dev/sda: 122.9 GB, 122942324736 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14334   115137823+  83  Linux
/dev/sda2           14335       14946     4915890    5  Extended
/dev/sda5           14335       14946     4915858+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS

I have edited menu.lst to add the fol. lines:
title Windows XP Pro
root(hd1, 0)
makeactive
chainloader+1

Now when I start boot, GRUB lists the Windows XP Pro option, but when I select it, nothing happens.

I can boot into Ubuntu 8.10 just fine. Also, when I disconnect the Ubuntu drive, I can boot into the XP partition normally.

I probably should mention that I have installed Windows XP separately when the Ubuntu drive was not connected. Similarly I disconnected the Windows XP drive when I installed Ubuntu.

How do I get the Windows dual boot working from GRUB? Any tips as to what I am doing wrong?

Thanks in advance.

---

### Post by twin-08 on 2009-04-21
try switching the sata ports xp drive to port 1 and linux port 2

---

