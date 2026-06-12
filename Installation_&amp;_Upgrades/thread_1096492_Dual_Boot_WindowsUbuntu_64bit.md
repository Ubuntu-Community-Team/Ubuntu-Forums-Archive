---
title: "Dual Boot Windows/Ubuntu 64bit"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by dongiuseppe2684 on 2009-03-15
I have Windows x64 and Ubuntu x64 currently on my hard drive.  Everything is working fine but my /boot/grub/stage1 file is located on (hd0,4).  Why is it there?  Can someone explain the number that grub uses with (hd0,?)?

Some other info:  I had installed Windows 32bit then ubuntu x64 on my computer.  I then deleted my Windows partition and installed Windows 64bit.  This wiped the MBR and I had to reconfigure grub so I can dual boot. So when I looked for the stage1 file it was on (hd0,4).  Also in menu.lst Windows is on (hd0,0).  So my question is where is (hd0,1-3)?  And is there anything that I should check?

---

### Post by Mark Phelps on 2009-03-15
To find all the partitions, do an "sudo fdisk -lu", that's a lower-case L not a number one.

---

### Post by dongiuseppe2684 on 2009-03-15
Thank you for the fdisk command.  I did check this out in my Gparted utility and it does reflect same as the output from fdisk -lu.   
It is as follows:
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   260863469   130431703+   7  HPFS/NTFS
/dev/sda2       260863470   586067264   162601897+   5  Extended
/dev/sda5       260863533   572781509   155958988+  83  Linux
/dev/sda6       572781573   586067264     6642846   82  Linux swap / Solaris

This is all good info but I need to know what the (hd0,?) is for.  My disk only has two partitions.  One is for the NTFS and the other is for Ubuntu which Ubuntu has two other internal partitions for the swap and extended.

---

### Post by Hobgoblin on 2009-03-15
> **dongiuseppe2684 said:**
> Thank you for the fdisk command.  I did check this out in my Gparted utility and it does reflect same as the output from fdisk -lu.   
It is as follows:
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   260863469   130431703+   7  HPFS/NTFS
/dev/sda2       260863470   586067264   162601897+   5  Extended
/dev/sda5       260863533   572781509   155958988+  83  Linux
/dev/sda6       572781573   586067264     6642846   82  Linux swap / Solaris

This is all good info but I need to know what the (hd0,?) is for.  My disk only has two partitions.  One is for the NTFS and the other is for Ubuntu which Ubuntu has two other internal partitions for the swap and extended.

hd0,4 is /dev/sda5, i.e 5th partition (counting from 0) on the first drive.

At some time you have changed the partitions and removed sda3 and sda4.

---

