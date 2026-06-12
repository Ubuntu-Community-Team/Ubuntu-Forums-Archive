---
title: "Suggestions for partitioning a 16GB netbook drive?"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by Nick255 on 2009-06-29
Any idea what the best way to partition a 16GB hard drive (for a netbook) would be?  I was thinking about 1GB for hibernation, 500MB for /, 5GB for /usr and the rest for /home.  Is that good or would it be better to do it some other way?  I would prefer to avoid having /usr on / as it is not possible to cancel a fsck on / (you just get a prompt to either enter the root password for single user mode or reboot).

---

### Post by milton1 on 2009-06-29
Is this a standard drive or a flash drive? If it is a flash drive (as many netbooks are) I would skip the swap area, and thus disable hibernate. Otherwise your system may be writing to the drive more often than you would like, shortening its lifespan.

---

### Post by raymondh on 2009-06-29
> **Nick255 said:**
> Any idea what the best way to partition a 16GB hard drive (for a netbook) would be?  I was thinking about 1GB for hibernation, 500MB for /, 5GB for /usr and the rest for /home.  Is that good or would it be better to do it some other way?  I would prefer to avoid having /usr on / as it is not possible to cancel a fsck on / (you just get a prompt to either enter the root password for single user mode or reboot).

Just my thoughts ..

Below 25 GB, I would just use a straight-up install (no /home, no /usr).  Your standard install (from liveCD) will take up about 4GB. I think 500mb is too small for root (/). You will see that when you make your first update post-install.

To continue with my thoughts, that leaves 12 GB for media files, settings, etc less any "administrative deductions" and post tweaks/installs.  Effectively, you will have only about 10 GB for /home and /usr. 

Again, just my thoughts.  Now, if you really need to have /home and /usr ....

1GB for swap (if you need to hibernate)
8GB for root
rest for /home and /usr

---

