---
title: "Formating a EXT2 partition back to an NTFS partition"
date: 2005-12-11
forum: Installation &amp; Upgrades
---

### Post by tromik on 2005-12-11
I have Ubuntu installed at the moment, but I'd like the hard drive space back, and am actually quite happy with the Live CD. What's the best/easiest way to turn an EXT2 partition back into a NTFS partition? I don't car if I lose anything on the partition, but I don't want the other partition on the hard drive altered.

---

### Post by aysiu on 2005-12-11
To delete the Ext2 partition, pop the live CD in, install and run GParted, and delete it.

Afterwards, I think the NTFS formatting can be done in Windows, actually.

Something like Start Menu > Control Panel > Administrative Tools > Disk Management (I'm going off memory here).

---

### Post by tromik on 2005-12-11
I am using 5.04, and even after updating the repositories, apt-get install gparted doesn't seem to work, although its present in the Starter Guide. Is this because I'm using the Live CD and the new repositories aren't actually being saved?

---

### Post by aysiu on 2005-12-11
I think gparted is only in Breezy.
How about if you do this? ```
sudo apt-get install parted
```

---

### Post by tromik on 2005-12-11
Thanks for the help. Now I have another question. I've deleted the ext3 partition without altering grub, and now I get an error when the computer boots. How can I make it boot back into Windows by default?

---

### Post by tromik on 2005-12-11
Ok, I reinstalled Ubuntu 5.04 (ext3) and updated it. Now I have a choice of booting between Ubuntu and Windows, and they both boot fine. What's the best way to remove Ubuntu, and also, how to I alter the Grub so that Windows will boot?

---

