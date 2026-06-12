---
title: "hard disk gone AWOL ?"
date: 2010-12-17
forum: Hardware
---

### Post by pdc124 on 2010-12-17
I want to add a 40GB HD that ive had for a while, that has a linux FS on it ,with the intention of reformatting and using it as storage. 

When its plugged in and jumpered as a slave, the BIOS recognises it, but the system fails to boot. 
Starting from  live CD doesnt consistently work. 

I tried SystemRescueCD and the system hung with 
ata2 SRST failed (errNo=-16) message. 

A Ubuntu 10 liveCD stopped with 
CPU#0 soft lockup system stuck for 61s (plymouthd:1065) 

Adding nomodeset option to the liveCD kernel  boot gets the machine started from the liveCD , but there is no slave disk detected in dmesg and only sda appears  in the disk utilities - so i cant test it .

Is it a configuration problem or is it an ex-Hard disk that I am trying to resurrect ?

---

### Post by efflandt on 2010-12-17
You did not say how your other drive is jumpered.  If both drives are on the same cable, and there are no markings on the cable as to which drive is which, the other drive may need to be jumpered as "master".  If the cable tells which drive is which, then they should both be jumpered "cable select" (CSEL).

If you plugged the cable in upside down, the drive may just spin continuously (did that once).

Does **sudo fdisk -l** (small L) show any sign of the other drive?  If the electronics on the drive are working and properly jumpered and connected, that should at least show something, even if the disk is corrupted and cannot identify partitions.

---

### Post by pdc124 on 2010-12-17
This one( disk A) is jumpered as the slave the other (disk B) is jumpered as the master. 


Without  A , B starts. 

With A (slave)  , B (master) doesnt start. 

Booting from a live CD (ubuntu10 and SystemRescueCD)  I can find the error messages ive listed.

---

