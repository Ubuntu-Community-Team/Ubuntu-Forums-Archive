---
title: "Disk corruption on IBM T40 while installing"
date: 2008-10-31
forum: Hardware
---

### Post by glasper on 2008-10-31
I'm having trouble setting up a dual boot system on my IBM Thinkpad T40.  It has been upgraded to a 120 GB hard drive, and as part of the upgrade, the Hidden Protected Area of the original disk (the system recovery area) was copied over to the new drive using the Fiesta utility, and Windows installed from that.  That worked fine, but I have discovered that if I try to install Ubuntu by resizing the NTFS partition created by the Windows installer, the partition resizer in the Ubuntu installer appears to corrupt both the NTFS partition /and/ the recovery area.  This shouldn't even be possible as the HPA is supposed to be, yes, hidden and protected. 

I have tried zeroing the disk, booting a Ubuntu live CD, reinstalling the HPA using Fiesta, and partitioning it into NTFS, Swap and Linux partitions manually using fdisk, then booting into the HPA and running the system recovery tool, but if I do this, then the Windows installer complains about an invalid partition table, and instead of creating an NTFS partition, creates what appears to be a wrongly formatted Fat32 partition (in that it doesn't use all the space allocated to it in the partition.)

---

### Post by Fir3chi3f on 2008-10-31
Have you tried just a gparted live disk to resize the windows? then install ubuntu?

---

### Post by glasper on 2008-11-02
Thanks, I used the Gparted Live CD and was careful not to overwrite the free space where the HPA is located.  Windows was really unhappy with being resized and insisted on doing a filesystem check on being booted, but nothing appears to be corrupted.

---

