---
title: "Seeing Windows drives in ubuntu and vice versa"
date: 2005-12-27
forum: Installation &amp; Upgrades
---

### Post by swregulator on 2005-12-27
I installed ubuntu on a 2nd hard drive.  This drive no longer appears in explorer when I boot Windows.  Can I save files to it?  

Same question in reverse.  Where can I find my Windows drive (labelled C: in Windows) from ubuntu.  Can I save files to it?

---

### Post by amohanty on 2005-12-27
AFAIK the only software to view ext2/3 filesystems is explore2fs ([http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)). Even using that you cannot write to your linux drives. If you installed the default Ubuntu installation, you should be able to view and read from your linux partitions, but will not be able write to it.

Re: your windows drives from ubuntu, you have to manually mount it or set it up in /etc/fstab to be able to view it. In this case too if you have an NTFS partition (Default win xp setup) it is advised that you not write to it, since write support is dodgy. Search the forums for mount ntfs and you will find lots of answers for this one.

HTH
AM

---

### Post by FlyDoc on 2005-12-28
Another alternative for Windows is Ext2 Installable File System For Windows at

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

It provides Windows NT4.0/2000/XP with full access to Linux Ext2/Ext3 volumes (read access and write access).

---

### Post by noeluylee on 2005-12-28
You can use Fat32 so your windows and linux will have write access to it. I just did that with my data partition on my laptop, so I could share that partition, because I have dual boot windows xp and ubuntu.

---

