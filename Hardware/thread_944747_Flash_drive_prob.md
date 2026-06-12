---
title: "Flash drive prob"
date: 2008-10-11
forum: Hardware
---

### Post by swapnil on 2008-10-11
A while ago, while using public PCs in my college, I pulled out my pen drive without using the "Remove Safely" option in Windows Vista. That corrupted the device probably because of viruses in the background. I'm unable to use it. In partition editors like GParted, it showed only 4MB of disk space while I had 16GB earlier. It's a Transcend JetFlash.
To solve it myself, I used fdisk and loaded the pen drive through the sudo command. I managed to delete the partitions and the partition table, but couldn't manage to make one.
While creating a new partition table, fdisk killed itself after saving something that I didn't understand.
However, now when I load the device using fdisk, it gives me errors like these ...

You will not be able to write the partition table.

Unable to read /dev/sdc

And here's the dmesg output [file]("http://technil.com/files/dmesg.txt"). The pen drive problem is around line 17.115959

Yep, just these 2/3 lines. What should I do? How to get 16 GB back?
Help...

---

### Post by linux_lover69 on 2008-10-11
> **swapnil said:**
> A while ago, while using public PCs in my college, I pulled out my pen drive without using the "Remove Safely" option in Windows Vista. That corrupted the device probably because of viruses in the background. I'm unable to use it. In partition editors like GParted, it showed only 4MB of disk space while I had 16GB earlier. It's a Transcend JetFlash.
To solve it myself, I used fdisk and loaded the pen drive through the sudo command. I managed to delete the partitions and the partition table, but couldn't manage to make one.
While creating a new partition table, fdisk killed itself after saving something that I didn't understand.
However, now when I load the device using fdisk, it gives me errors like these ...

You will not be able to write the partition table.

Unable to read /dev/sdc

And here's the dmesg output [file]("http://technil.com/files/dmesg.txt"). The pen drive problem is around line 17.115959

Yep, just these 2/3 lines. What should I do? How to get 16 GB back?
Help...
The dmesg output file link does not work. Also have you tried using gparted or any other partition editor.

---

### Post by swapnil on 2008-10-11
This is the link - [http://technil.com/files/dmesg.txt](http://technil.com/files/dmesg.txt)

Yes. I've tried GParted and it doesn't show any option over there. I mean it doesn't read after I made it go through fdisk.

---

### Post by linux_lover69 on 2008-10-11
It says you have write protect on. On some flash drives theres a little button like thing on the side to turn write protection on and off. See if its on lock.

---

### Post by linux_lover69 on 2008-10-11
This guy here sounds like he has a similar problem. Maybe theres an answer in here.
[http://www.hardwareanalysis.com/content/topic/46202/](http://www.hardwareanalysis.com/content/topic/46202/)

---

### Post by swapnil on 2008-10-11
Thanks a bunch ... I found a new way to solve the prob.

---

### Post by linux_lover69 on 2008-10-11
your welcome

---

