---
title: "Second internal disk drive"
date: 2009-09-01
forum: Hardware
---

### Post by it99 on 2009-09-01
I installed a second Hard Drive on my computer. The BIOS recognizes it as the Primary slave. What I want is the new drive to be just an seemless extension of the existing drive. So instead of 2 80 Gig drives it looks like one 160 Gig drive. What do I have to do cofigure the drives and do I have to do anything special with Ubuntu?
I think the drives might be Sada? There is a /dev/sda,sda1,sda2,sda5. This is the first time I've done this so I have no idea of what to do. Thank you very much for your help!!!

---

### Post by mdmarmer on 2009-09-01
It's not possible to treat two drives as a single drive. All OS will recognize each drive separately.

Partition the new drive with gparted.  If the first drive shows up as sda, the new drive will probably be sdb.  Most newer kernels recognize all drives as sd rather than hd, regardless of whether they are SATA or IDE.

---

### Post by it99 on 2009-09-01
Thank you very much!
 
I formatted the second drive and mounted it to /tmp.
My first drive was mounted at /
Whenever I mount the second drive to /tmp most things stop working on the computer. I can't bring system performance, 'Computer' or anything. I have to unmount it in order for it to work.  
What am I doing wrong??
 
Thanks

---

### Post by trundlenut on 2009-09-01
I think /tmp is used by ubuntu so by mounting the other drive as /tmp all kinds of weird things will probably happen.  Mount it a /storage or something else.

As for making the two drives appear as one large one you need to look at software raid or logical volume management (LVM).  Try searching for these on here.

---

