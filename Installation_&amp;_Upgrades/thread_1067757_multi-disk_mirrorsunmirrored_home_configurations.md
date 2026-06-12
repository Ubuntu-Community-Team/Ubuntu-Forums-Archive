---
title: "multi-disk mirrors/unmirrored home configurations"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by dnel on 2009-02-12
Hi, I've recently gone through a hard disk failure and a major PC upgrade in the last few weeks and I'm considering how to rebuild my disk/file-system structure which is a complex issue so I'd like to tap the collective experience for advice.

I have 4 disks
250GB Samsung
250GB Samsung
500GB Seagate
500GB Seagate (once I get the RMA replacement)

I currently host my home directories on the 250GB disks in hardware fakeraid1, I boot off a 5th disk which will be removed from the PC after the work.

What I'd like to do is eliminate the hardware raid and use my only new on-board SATA ports. Having gone from 3 different RAID controllers pre-upgrade I'd like to get rid of the normal hardware raid cross-compatibility issues and use Linux software RAID and/or LVM2.

My current thinking is to backup important data onto the new 500GB disk and erase the remaining 3 disks. I will then create an LVM group incorporating the 3 physical volumes. I'd like to create mirrored LVM volumes for the OS and for the Home directories and then the remaining disk space will be non-mirrored LVM file-storage probably mounted off /media. After wards I will restore the data from the 500GB disk backup and bring the 4th disk into the LVM group and increase the LV sizes.

I guess my questions are:

1.Is this kind of setup possible?
2.Would you recommend an alternative configuration?
3.If I lose a disk will the non-mirrored area be completely compromised or will I just lose a proportion of the hosted files?
4.Can anyone point me towards good and up-to-date documentation on mirrored LVM configurations?
5.Any other pointers or good case examples of multi-disk mirrored home configurations?
6.Seen as you apparently can not boot from LVM, can I create a mirrored boot partition using Linux RAID so that at least the system is not compromised by losing the /boot partition?

TIA
Dave

---

### Post by dnel on 2009-02-15
After a bit of research and pondering I've decided on a simpler setup using a RAID1 mirror of a 250+500gig disk. To do this however I will need to using one of the 250GB disks as an ark of all my data to copy over to the new array. My thoughts for this process are:

1. Copy all data to 250GB disks + made hard backups on DVD
2. Remove one 250GB disk breaking existing RAID1 array, move to on-board controller
3. Create a md0 array using a newly blanked 250GB disk and a blank 500GB disk.
4. Reinstall Ubuntu onto new md0 array.
5. Copy data off 250GB disk into new md0 Ubuntu installation
6. Create md1 out of 2nd 250GB + 500GB disks
7. Set up mirroring between md0 and md1 and rebuild array

Questions I have now however are:

1. Can Ubuntu boot off a md array? 
           ->I'm vaguely aware it can't boot off LVM but I can create a small boot partition at the start for this.
2. Will this process work?

I'll also be using LVM on the RAID array to stripe the disks but this seems to be the least complicated bit. I'm still a bit shaky on how mdadm works so I could be completely wrong, if so please let me know before I do something stupid :)

---

