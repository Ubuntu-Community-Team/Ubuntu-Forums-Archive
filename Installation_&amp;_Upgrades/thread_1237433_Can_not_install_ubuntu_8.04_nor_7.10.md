---
title: "Can not install ubuntu 8.04 nor 7.10"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by bearnais on 2009-08-11
I was running ubuntu 8.04 when after an update of software when I got into a grub problem (which i could not solve). I erased all partitions and want to have a clean ubuntu installation, no longer dual boot.
 
When I try to install, just before the screen with the bird come on I get a message (but i can not read it, refers to firmware). But that is not the reason for me to ask for help.
 
When I try to install ubuntu I get as far as the partitioning. I have tried both guided and manual and each time I reach to "creating ext 3 in / formatting". Then I get the message "the attempt to mount a file system with type ext3 in SCSI 1 (0,0,0) partition #1 (sda) at / failed. You may resume partitioning from .... I go back and try again but I get the same message over again.

I have tried sudo fdisk -l with the live CD. But that does not give any output. 
 
I have got no clue why this is happing. Until the breakdown I ran 8.04 with great joy for months. Now I am getting very frustrated.
 
I must be doing something wrong. Please advise. Thank you.

---

### Post by phillw on 2009-08-11
The firmware error is of concern.  I'd suggest that you try using the cd in 'live' mode to make sure it is happy.

If it is, get the utility for your make of hard-disk from the manufacturers site & it should have options to test & format your disk. - I'd do both.

hope this is of help.

Regards,

Phill.

---

### Post by bearnais on 2009-08-11
I had this problem with two different hard disks. I will test them and see.

Thanks for the advice.

Philippe

---

### Post by bearnais on 2009-08-12
I put in a new hard disk, tested and found to be OK. Still when I tried to install, I still got the message at the partitioner that it could not detect a device. In my BIOS it is there. Anybody knows what could be the problem?

---

