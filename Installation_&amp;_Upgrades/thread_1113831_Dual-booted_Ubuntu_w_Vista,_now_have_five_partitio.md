---
title: "Dual-booted Ubuntu w Vista, now have five partitions..."
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by cAlpha on 2009-04-02
1 - Healthy (EISA Configuration) / 71MB
2 - Healthy (Primary Partition) - Recovery (D: ) / 10GB NFTS
3 - Healthy (System, Boot, Page File, etc.) - OS (C: ) / 54.19GB NFTS 
4 - Unallocated / 7.77GB
5 - Healthy (Primary Partition) / 2.5GB

Now, I've successfully installed Ubuntu 8.04 to dual-boot with Windows Vista.  Correct me if I'm wrong, but going through the automatic Ubuntu installation would have loaded the Ubuntu OS on (5) with the original Vista OS on (3).  

I've been able to mount (2) and (3) within Ubuntu, and can access files, but for the sake of cleanliness, I'd like to use one of the partitions as a shared location for general files (eg, pictures, Matlab/R code, assorted documents, etc.), while still leaving all Vista-specific files inaccessible to Ubuntu, and vice versa.  

Broadly, I think of having one partition for Vista OS files, one for Ubuntu OS files, one for files that can be used within either OS, and one for the recovery partition.  

How do I go about adjusting partition size, format and contents to make this happen?

---

### Post by Mark Phelps on 2009-04-02
If you want to have a shared data partition, you might want to shrink the Vista partion to make more room for it.  I would strong advise AGAINST making your Vista OS a shared partition.  But you seem to be OK with that already.

I wouldn't mess with (1) or (2) at all.

If you want to shrink (3) be sure to use the Vista Disk Management utility to do that.  If you have problems getting it to shrink, see the following link:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

I would recommend allocating (4) as your shared drive and formatting it as NTFS.  That will allow both Vista and Ubuntu to read and write it.  Make sure you have the ntfs-3g package installed in Ubuntu for NTFS access.

---

### Post by cAlpha on 2009-04-02
Thanks for your reply.  That sounds about like what I was planning, but when I use the New Simple Volume Wizard in Vista to format (4) as NFTS, I was given an error that I'm only allowed two NFTS partitions.  Was this related to your suggestion about nfts-3g?

Furthermore, should I try to shrink/expand any of (3), (4) or (5) to better achieve my objective (ie, Vista doesn't need ~55GB, and extra GB for the shared partition and Ubuntu partition would be useful)?

Thanks a bunch for your input.

---

### Post by ronparent on 2009-04-02
Not to interfear since you are already getting good advise. I believe that windows in general will deal with only two primay partions (which are (2) and (3)). I believe you can create an extended partion within which you would be able to create as many ntfs partions as you please. ntfs-3g still applies.

---

### Post by cAlpha on 2009-04-02
That's what I thought, which is why I'm a bit confused.  The recovery drive (NFTS 1) isn't to be meddled with and the other NFTS partition contains Vista OS and associated files, which I'd like to keep completely separate from Ubuntu.  If I can't create an addition NFTS partition, I can create an extended partition within the Vista OS NFTS partition that would act as a shared store for Vista and Ubuntu files, but wouldn't that violate the 'keep Vista and Ubuntu OS files separate each other and everything else' requirement?  Appreciate your input.

---

### Post by ronparent on 2009-04-02
The extended partition would be created in rhe unallocated space. Within that you can create an indiviual drive or drives which can be formated ntfs or fat32 which both windows and ubuntu can read.

---

### Post by cAlpha on 2009-04-02
OK, so I CAN format the 'Unallocated' partition as FAT32 for use by both Ubuntu and Vista?  

Assuming that's the case, I'd be able to do this via the New Simple Volume Wizard in Vista, correct?  

Also, any thoughts about shrinking or expanding the volume of any of my current partitions?  

Recall:
(3) **Vista**: OS (C: ) / 54.19GB
(4) **Unallocated** / 7.77GB
(5) **Ubuntu (I think)**: Healthy (Primary Partition) / 2.5GB


I really appreciate all of your input, guys.

---

### Post by ronparent on 2009-04-02
I admit I haven't yet used the New Simple Volume Wizard in Vista, but it should work, as well as gparted the ubuntu partion editor.

Your allocation for Ubuntu may be a bit on the skimpy side, but usable unless you plan to use it extensively. Your allocation for the data partition is dependent on how much you need (planning for adequate headroom for expansion).

---

### Post by Mark Phelps on 2009-04-02
> **cAlpha said:**
> Thanks for your reply.  That sounds about like what I was planning, but when I use the New Simple Volume Wizard in Vista to format (4) as NFTS, I was given an error that I'm only allowed two NFTS partitions.  Was this related to your suggestion about nfts-3g?

Furthermore, should I try to shrink/expand any of (3), (4) or (5) to better achieve my objective (ie, Vista doesn't need ~55GB, and extra GB for the shared partition and Ubuntu partition would be useful)?

Thanks a bunch for your input.

You can use GParted LiveCD or boot from the Ubuntu LiveCD and use the Partition Editor to reformat your unallocated space as NTFS.  Just don't mess with the other NTFS partitions using GParted.

---

### Post by cAlpha on 2009-04-03
OK, so it appears is if Vista limits the number of primary partitions I'm able to create to 4, so when I try to create a fifth using the Unallocated partition, I get an error that the "disk already contains the maximum number of partitions".

The fix I've seen for this is to combine/create partitions such that there exists a parition for EISA ((1) in the original post), one for Vista OS (3), one for shared files (4), and one for Ubuntu OS (5).

I guess one way to accomplish this would be to simply combine the Recovery partition (2) with the currently unallocated partition (4).  I should be able to extend the volume of (2) to incorporate (4) and achieve my aim, correct?  Is there any reason not to do this? 

'Extend Volume' is grayed out for the Recovery partition within Disk Management though.  How do I get around this?

---

### Post by Mark Phelps on 2009-04-04
> **cAlpha said:**
> OK, so it appears is if Vista limits the number of primary partitions I'm able to create to 4.
That's not a Vista limitation.

> 
The fix I've seen for this is to combine/create partitions such that there exists a parition for EISA ((1) in the original post), one for Vista OS (3), one for shared files (4), and one for Ubuntu OS (5).

I guess one way to accomplish this would be to simply combine the Recovery partition (2) with the currently unallocated partition (4). 

No, No, No.  Do NOT mess with the recovery partition. If you do, you will not be able to recovery your Vista installation.

You'll probably need to reinstall Ubuntu because what you want to do is the following:
1) Shrink (3) to make some room -- be sure to use the Vista Disk Management tool to do this.
2) Remove (5) -- you can use GParted to do this
3) Created an Extended partition to fill the now unallocated space at the end of the volume
4) Create an Ext3 partition in the Extended partition to hold Ubuntu
5) Create an NTFS partition in the Extended partition for data sharing
6) Install Ubuntu to the Ext3 partition

---

