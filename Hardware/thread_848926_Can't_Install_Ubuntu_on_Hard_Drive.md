---
title: "Can't Install Ubuntu on Hard Drive"
date: 2008-07-03
forum: Hardware
---

### Post by paulysan on 2008-07-03
Hello, I just recently bought a new 320Gb HDD for my laptop.  Before I installed any OS's on it, I used Gparted to split my drive into three partitions - 1 for Windows Vista, 1 for Ubuntu, and 1 for Data.  

I installed Vista on the first partition fine, and have encountered no problems, however, when I go to install Ubuntu and get to step 4 (Prepare Disk Space, it only recognizes one drive in the guided resize option, the third one (Data).  However, I can go to manual and look at the three drives, but when I try and select the drive I want to install Ubuntu on, it says "No root file system is defined.  Please correct this from the partitioning menu".

It also might be worth mentioning that all drives are in NTFS format.  If any of you guys can help me, please do.

---

### Post by logos34 on 2008-07-04
> **paulysan said:**
> it only recognizes one drive in the guided resize option, the third one (Data).  However, I can go to manual and look at the three drives, but when I try and select the drive I want to install Ubuntu on, it says "No root file system is defined.  Please correct this from the partitioning menu".

It also might be worth mentioning that all drives are in NTFS format

You have to set the mountpoint to '/'.  Format it ext3

Or else go back to the desktop, system>admin>partition editor (Gparted)

Delete the ubuntu partition and run the installer again.  Select 'Guided--use largest continuous free space'.  If it chooses the empty space of the deleted partition, accept.

---

