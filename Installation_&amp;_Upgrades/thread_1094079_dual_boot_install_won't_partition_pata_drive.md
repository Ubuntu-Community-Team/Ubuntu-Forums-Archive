---
title: "dual boot install won't partition pata drive"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by raypsi on 2009-03-12
I gots [B]asus a7v mb
           western digital 80gig pata HD
            526meg pc133 ram[/B]
I also bought a unbuntu cd 8.10
when installing for a dual boot on the HD it goes to partition and stays at 0% install for quite some time. Finally it comes back **partitioning aborted cannot write to drive**

I did a sudo fdisk -l from the live version, and got this:

[B] Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS[/B]

Lastly on my second attempt before install I defragged and chkdsk the drive in windows XP pro that took 5 hrs. And partitioning with ubuntu still aborted.

Now I try and go into windows to see if I can maybe partition another section in that drive with windows XP pro but no it goes to chkdsk I try to do a cancel chkdsk and it hangs. on  reboot it wants to do chkdsk and still hangs on cancel chkdsk.

Is my only hope to put this HD on another system and partition it there?

---

### Post by taurus on 2009-03-12
Can you use gparted (System -> Administration -> Partition Editor) from Ubuntu LiveCD to shrink your ntfs partition, creating an unallocated space at the end.  Then see if the installer would use that unallocated space when you get to the partition part (Step 4 out of 7)?  

Of course, back up your important files on windows first just in case.

---

### Post by raypsi on 2009-03-12
Sry OM: but the **Gparted version 0.3.5** won't do anything to an **NTFS formatted disk except detect it**. I looked under features and detection is the only thing it lists, But according to the Gparted web site under features it should do it all to an NTFS formatted drive guess I got to get 0.4.3 and try agin.
thanks

---

### Post by taurus on 2009-03-12
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by kernelCompile on 2009-03-12
> **raypsi said:**
> I gots [B]asus a7v mb
           western digital 80gig pata HD
            526meg pc133 ram[/B]
I also bought a unbuntu cd 8.10
when installing for a dual boot on the HD it goes to partition and stays at 0% install for quite some time. Finally it comes back **partitioning aborted cannot write to drive**

I did a sudo fdisk -l from the live version, and got this:

[B] Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS[/B]

Lastly on my second attempt before install I defragged and chkdsk the drive in windows XP pro that took 5 hrs. And partitioning with ubuntu still aborted.

Now I try and go into windows to see if I can maybe partition another section in that drive with windows XP pro but no it goes to chkdsk I try to do a cancel chkdsk and it hangs. on  reboot it wants to do chkdsk and still hangs on cancel chkdsk.

Is my only hope to put this HD on another system and partition it there?

Chkdsk failing to complete on your Windows file system is a very bad sign. It is likely that you have either a seriously hosed file system or a failing hard drive. You may need to backup files and reformat/reinstall Windows, or replace the hard drive. You will probably not be able to resize you Windows file system without correcting the file system problems.

---

