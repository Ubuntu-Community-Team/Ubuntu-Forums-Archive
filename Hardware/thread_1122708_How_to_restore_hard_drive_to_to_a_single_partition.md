---
title: "How to restore hard drive to to a single partition?"
date: 2009-04-11
forum: Hardware
---

### Post by mzaiemo on 2009-04-11
Hi all,

Lately i have install ubuntu intrepid ibex with ~2G swap, ~20G ubuntu system(ext3) and a partition for document(ntfs). for some reason i want to uninstall ubuntu..my question is:

1) How to restore swap, ext3 and ntfs into single partition(ntfs) leaving my ntfs intact?

2) if i have successfully install ubuntu intrepid, how do i install fresh jacklope? i mean do i have to delete swap and ext3 leaving my ntfs data untouch? and please tell me how to delete them.can i just delete using Gparted and create new swap+ext3 and then install ubuntu?

thanks,

---

### Post by Ericyzfr1 on 2009-04-11
1) you can use the Gparted live cd to restore to a single ntfs partition.
2) you can modify your partition during Ubuntu installation

---

### Post by unutbu on 2009-04-11
> can i just delete using Gparted and create new swap+ext3 and then install ubuntu?

Precisely. You can only delete partitions that are not in use, however, so you'll have to 
boot from a LiveCD. Launch GParted, and delete the Linux and swap partitions, leaving the NTFS untouched.

When you choose to install Jaunty Jackalope, select "Manual" (rather than "Guided") partitioning.
It will allow you to create and/or select which partition you want to use as the Linux partition. Just make sure there is no checkbox telling the installer to format the NTFS partition.

---

### Post by mzaiemo on 2009-04-11
Precisely. You can only delete partitions that are not in use, however, so you'll have to 
boot from a LiveCD. Launch GParted, and delete the Linux and swap partitions, leaving the NTFS untouched.

When you choose to install Jaunty Jackalope, select "Manual" (rather than "Guided") partitioning.
It will allow you to create and/or select which partition you want to use as the Linux partition. Just make sure there is no checkbox telling the installer to format the NTFS partition.

Thanks,

1) yes, but how do i merge both ntfs?
2) thanks, do i have to delete swap also? i'm sure i have to delete ext3..

---

### Post by unutbu on 2009-04-11
I'm not sure I understand your questions. Correct me if I've misunderstood.

(1) You have 

Swap 	 2GB
Intrepid 20GB
NTFS	 ?

And you want to create one big NTFS partition? Leaving your data intact?

In this case, boot the LiveCD, launch GParted (System>Admin>Partition Editor)

Click to select the Swap partition. Click the Delete button. 
Click to select the Linux partition. Click the Delete button. 
Click to select the NTFS partition. Click the Resize button. Expand to use all the space.
Click the Apply button to tell GParted to commence the above operations.



(2) You have 

Swap 	 2GB
Intrepid 20GB
NTFS	 ?

And this time you want to install Jaunty in place of Intrepid? 
In this case, you boot the Jaunty LiveCD or Alternate installer CD.
When you get to the disk partitioning step, select "Manual" rather than "Guided" partitioning.

Select the partition which currently contains Intrepid, and tell the partitioner to use this partition as the root partition. You do this by telling the partitioner to mount the partition at /. (I believe, in the LiveCD installer, you do this by using a drop-down combo box labeled "Mount point".)

Similarly, you tell the installer to use the swap partition as swap.

The installer will reformat the Intrepid and swap partitions. You do not need to delete them beforehand.

---

### Post by fourthofjuly on 2009-04-11
> **mzaiemo said:**
> Hi all,

Lately i have install ubuntu intrepid ibex with ~2G swap, ~20G ubuntu system(ext3) and a partition for document(ntfs). for some reason i want to uninstall ubuntu..my question is:

1) How to restore swap, ext3 and ntfs into single partition(ntfs) leaving my ntfs intact?

2) if i have successfully install ubuntu intrepid, how do i install fresh jacklope? i mean do i have to delete swap and ext3 leaving my ntfs data untouch? and please tell me how to delete them.can i just delete using Gparted and create new swap+ext3 and then install ubuntu?

thanks,
with the jj install disk, the partitioner will ask which partitions you would like to install to, where you may delete your existing ext3 and swap partitions and re-create new ext3 and swap partitions for jj in the free space thus created...

**BACKUP of your existing data on the ntfs partitions is strongly recommended even though you wish to leave the partition intact...**

however, since jj is still in beta testing phase, i would rather wait a few days for the stable release...

---

### Post by mzaiemo on 2009-04-11
Thanks for ur kindly help..guest i have no choice but to tey an eror..hehe :-P

---

### Post by mzaiemo on 2009-04-11
Thanks for ur kindly help..guest i have no choice but to try an error..hehe :-P

---

