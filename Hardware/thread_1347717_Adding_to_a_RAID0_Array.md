---
title: "Adding to a RAID0 Array"
date: 2009-12-06
forum: Hardware
---

### Post by jbiggs12 on 2009-12-06
So after a fair amount of googling to no specific answer, I've given up and am moving to the ubuntu forums. My question is this: Say I have a 3-hdd RAID array, each drive being 1.5 tb. Am I wrong in assuming that simply plugging in another hard drive and adding it to the RAID configuration would be okay, without any loss of data whatsoever? Furthermore, if one drive starts to fail or I feel like upgrading it, could I clone the drive to a 2tb hard drive and have the RAID array still functioning? This is for my newest computer build; I want to be able to upgrade my parts and storage in the future with little to no hassle. Thanks!!

---

### Post by paulisdead on 2009-12-06
The steps to add a drive should be pretty much the same as this even though the directions are for RAID5 [http://scotgate.org/2006/07/03/growing-a-raid5-array-mdadm/](http://scotgate.org/2006/07/03/growing-a-raid5-array-mdadm/)

You can't remove drives or have hot spares in a RAID0, since it offers no fault tolerance, at all.  In fact RAID0 is less tolerant than a single drive, since 1 drive in the array fails, all the data is gone.  You might want to look into RAID5, since that costs the least amount of space, and can handle the loss of a single drive.  If you need really good write performance, RAID10 is better, but needs a minimum of 4 drives and costs you half your space.

You should be OK to add a drive without data loss, but you should back up everything first, just in case.  You would, after all, be expanding the array, and then resizing the filesystem, so there's always a chance something could go wrong.

---

### Post by jbiggs12 on 2009-12-06
Aha. I'm not entirely sure what RAID5 is, Wikipedia hasn't helped me much. Does it have the same storage space as a RAID0 array, or is it like RAID 10 or RAID01 in that it needs half of the data for a 2nd backup? The reason that I wanted a RAID0 array was for the huge amounts of space that was possible; I'm less interested in the thought of backing up because I'll catch the failure, clone the drive and replace it.

---

### Post by jbiggs12 on 2009-12-06
Nevermind, I understand perfectly now. SO for growing the array, would I have to add 2 extra hard drives instead of just simply one? Because from what I understand it needs an even number of hard disk drives.

---

### Post by paulisdead on 2009-12-06
RAID0 can use an odd number of disks, you wouldn't need to add them in pairs.

RAID5 is like RAID0, it stripes the data along all the available drives, making it very fast.  Except for one difference, it has additional parity data that allows for the array to continue functioning in the event of a failure.  The caveat of this, is that you lose all the space of one drive in the RAID5 array to parity.  This is only 1 drive worth of data, no matter how many drives you have in the array.  So 3x1TB drives in raid5 gives you 2TBs of usable space, and 4x1TB drives in a RAID5 would be 3TBs of space.  RAID5 can also use an odd number of drives, and doesn't need to be installed in pairs.  It does, however, need a minimum of 3 drives.

It's always nice to think you'll catch a failure before you start losing data, but quite often drives stop working with no warning, even if you have SMART enabled.  I highly recommend not keeping anything remotely important on a RAID0 array.  Like I said, RAID0 is less tolerant than a single drive, and the more drives you add to it, the more likely you will lose all the data on it.

Also, although any RAID level except RAID0 can protect against a drive failure, RAID is still not a backup, and you should backup your data regularly.  RAID doesn't protect against things like deletion, or say if the filesystem over the top of it gets completely corrupted.

---

### Post by jbiggs12 on 2009-12-07
Thanks for the tip! RAID5 will now be my top choice in my hdd configuration :) I appreciate your advice!

---

