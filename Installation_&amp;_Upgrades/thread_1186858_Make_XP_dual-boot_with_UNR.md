---
title: "Make XP dual-boot with UNR"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by sukelis on 2009-06-13
First, I apologize because I expect this has been answered - but I can't find it.  I've done some looking but this is such an active forum that finding what you want depends on being able to search for it and I haven't come up with the right search terms.

I have an Acer Aspire One netbook, which runs XP Home.  I would like to make it dual-boot with UNR.  I have never tried Ubuntu before, and have only limited experience with Linux, but have used Unix in a previous life.  I have lots of experience with desktops, but this is my first foray into laptops/netbooks.

My first issue is the partitioning, naturally.  I have already shrunk my XP partition and freed up half the (160GB) disk.  But this netbook comes with a 6GB recovery partition (hidden) as the 1st partition and then windows as the 2nd.  So, by default, Ubuntu will wind up in the inside, slow part of the disk.  

I have burned the recovery images to DVD, so I could delete the recovery partition, but 6GB doesn't seem like enough space.  And I think trying to have Linux partitions before and after the Windows partition is... not wise.  So, I'm thinking about moving the XP partition to the end of the disk and then deleting the recovery partition and creating an extended partition using all of the available disk space.  Since Windows insists on naming the first Primary partition as C, and naming extended/logical partitions after primary partitions, the installed XP should still find itself on C and be happy.  

I will probably need to re-create the MBR and boot files, depending on what I find when I unhide the partition.  But if I get that all sorted out and working before I start with UNR, then it should be all right, yes?   So, my first questions are:  Has anybody tried this before?  Is there any problem with deleting the recovery partition (after burning the discs)?

Thanks,

suke

---

### Post by 123456789123456789123456 on 2009-06-13
The main problem with deleting the recovery partition is that if you try to boot to XP without immediatly installing ubuntu, you will probable get the Incorrect partition table error, and a failed boot.  In which case you will need to tell xp to create a new partition table, and to fix MBR, and reinstall ntldr.  however if you have Ubuntu install GRUB onto MBR, you should not have any problems.  If you have freed up space at the end of the disk, you will not need to delete the recovery partition.  If you boot ubuntu, you will see that the disk has three partitons, hd0,1, recovery, hd0,2 XP, hd0,3 unused.  Ubuntu will then use hd0,3 for ubuntu boot primary, and hd0,5 as swap.  it will do this automatically, you just inform the installer, to use unused space.  Gurb will probably be installed onto the MBR deleting ntldr, which is fine, GRUB can take over boot, and boot both XP and Ubuntu without any problems.
It does not matter what partition the OS is installed on, should make absulutely no difference in speed, or performance.

---

