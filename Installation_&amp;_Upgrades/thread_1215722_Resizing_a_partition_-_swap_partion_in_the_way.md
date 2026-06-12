---
title: "Resizing a partition - swap partion in the way"
date: 2009-07-17
forum: Installation &amp; Upgrades
---

### Post by bldy_lunatic on 2009-07-17
Hi Everyone,

I have an Ubuntu 8.04 installation in a virtual machine (VMWare ESX 3.5) that I need to allocate more hard drive space to. I've added the extra space through VMWare, but I need to expand the partition inside the OS. This is normally a trivial task but in this case gparted won't expand the main partition because the swap partition is in the way. It does not appear to be possible to move the swap partition. Is it feasable to delete the swap partition, expand the main partition, and re-create the swap partition at the end of the disk again?

Thanks!

---

### Post by raymondh on 2009-07-17
> **bldy_lunatic said:**
> Hi Everyone,

I have an Ubuntu 8.04 installation in a virtual machine (VMWare ESX 3.5) that I need to allocate more hard drive space to. I've added the extra space through VMWare, but I need to expand the partition inside the OS. This is normally a trivial task but in this case gparted won't expand the main partition because the swap partition is in the way. It does not appear to be possible to move the swap partition. Is it feasable to delete the swap partition, expand the main partition, and re-create the swap partition at the end of the disk again?

Thanks!

Are you using gparted from the liveCD or your internal, ubuntu install?  Have you tried swap-off to move the swap partition or resize the main OS partition?  can you post a screenshot of gparted output?

See references:

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

---

### Post by bldy_lunatic on 2009-07-17
Thanks for the links, there is some good info there for me. 

In the Gparted documentation (the 2nd link) it mentions deleting the swap partition to get more space but it doesn't seem to get around to mentioning how to recreate it. Somehow I don't think Ubuntu is going to automatically recreate the swap partition. Unfortunately I'm new to Linux so I'm not really sure how to recreate the swap partition if I delete it.

---

### Post by raymondh on 2009-07-17
> **bldy_lunatic said:**
> Thanks for the links, there is some good info there for me. 

In the Gparted documentation (the 2nd link) it mentions deleting the swap partition to get more space but it doesn't seem to get around to mentioning how to recreate it. Somehow I don't think Ubuntu is going to automatically recreate the swap partition. Unfortunately I'm new to Linux so I'm not really sure how to recreate the swap partition if I delete it.

You can *manually* create a swap partition after feeing up space or, you can also create a swap file incase your HD does not have a swap partition.  Your choice.

Reference creating a swap FILE

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)   

Post a screnshot of your gparted output to help us visualize and see where to go. .... while I re-read your first post many times to understand better :)

---

### Post by bldy_lunatic on 2009-07-17
Ok, So I got it figured out. Here's the screenshot anyway and I'll tell you what I did in case anyone else runs into a similar issue.

The issue was that I couldn't move the swap (/dev/sda5) partition to the end of the drive in order to expand the /dev/sda1 partition. The reason the swap partition could not be moved was because it resides inside an extended partition /dev/sda2. The solution was a 4 step process. 

1. Expand the /dev/sda2 extended partition to the end of the drive.
2. Move the /dev/sda5 swap partition to the end of the (now larger) /dev/sda2 extended partition.
3. Shrink the /dev/sda2 extended partition back down to just the size of the /dev/sda5 swap partition.
4. Extend the /dev/sda1 ext3 partition to the end of the unallocated space.

The end result is the goal of extending the main partition of the Ubuntu Desktop by an additional 12GB

---

### Post by raymondh on 2009-07-17
> **bldy_lunatic said:**
> Ok, So I got it figured out. Here's the screenshot anyway and I'll tell you what I did in case anyone else runs into a similar issue.

The issue was that I couldn't move the swap (/dev/sda5) partition to the end of the drive in order to expand the /dev/sda1 partition. The reason the swap partition could not be moved was because it resides inside an extended partition /dev/sda2. The solution was a 4 step process. 

1. Expand the /dev/sda2 extended partition to the end of the drive.
2. Move the /dev/sda5 swap partition to the end of the (now larger) /dev/sda2 extended partition.
3. Shrink the /dev/sda2 extended partition back down to just the size of the /dev/sda5 swap partition.
4. Extend the /dev/sda1 ext3 partition to the end of the unallocated space.

The end result is the goal of extending the main partition of the Ubuntu Desktop by an additional 12GB

Cool.  Happy Ubuntu-ing.

---

