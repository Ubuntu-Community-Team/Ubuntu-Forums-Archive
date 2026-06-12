---
title: "lost /home after a fsck"
date: 2005-12-14
forum: Hardware &amp; Laptops
---

### Post by hamstah on 2005-12-14
Hi,
few days ago i installed windows and all went fine, i used explore2fs to view my files on my ubuntu partition, until one day when my /home was no more present in explore2fs, so i managed to boot on linux to find why, but as windows removed my mbr, I fdisk /mbr it but i wasnt able to boot on my partitions. So i used the live cd to try to activate my partitions. When i rebooted the partitions where still inactive.. I rebooted on the live cd and tried to mount my linux partition. I mounted it but my home directory was strange, with a ? in the permissions instead of d. As i found nothing else better, I did a fsck which take more than 24h... After this i remounted the partitions and my /home was no more here, as /lib.... My lost+found folder is full of files.

I want to recover my /home but i cant find any method for it. If someone can help me...

I just bought 2 virgins chicken to make voodoo sacrifice... please save them by helping me :]
thanks

---

### Post by stuporglue on 2005-12-14
> My lost+found folder is full of files.

When fsck runs, it puts files that were broken that it tried to save into lost+found. It sounds like something bad happened, and then when fsck was run it copied what it could to lost+found. 

If this is in any way an option, your best bet right now is to put another HD in your computer, and make it your new /home. Then copy over the files from lost+found and sort them as you have time.  Once you get them off of the borked partition, reformat the partition. 

I generally don't trust a partition once it's needed fsck. I get my stuff off ASAP, check for bad blocks, and reformat. Fsck is usefull, but it doesn't always fix everything. :(

Explore2fs and the likes are cool programs, but I don't trust them much anymore. I used a similar program for OSX for a couple of months and one day the drive similar to how you described. I ran fsck and got most of it back...but once bitten, twice shy.

---

