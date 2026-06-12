---
title: "[SOLVED] How can I list my available hard drives?"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by nelson.bolanos on 2007-10-10
Hi,

Just to let you know this is my first post, a friend of mine asked me a very interesting question, how can I list the number of hard drives connected to my Ubuntu 7.04? I can view the partitions once I have the disk identifier... but how can I get that identifier(/dev/hda for example), and whether is connected or not.

Thanks :D

---

### Post by nick_h on 2007-10-10
Type:
```
sudo fdisk -l
```

This will list partitions.  The first three letters will be the device followed by a partition number.

---

### Post by nelson.bolanos on 2007-10-10
Thanks, does this list more than one disk partitions? even if it's not formatted?

---

### Post by CowzRule on 2007-10-10
Yes, it does show all partitions from all disks

---

### Post by caled on 2007-10-10
Would typing df -h in bash not do a better job of displaying drive locations, mount points and available space?

---

### Post by nelson.bolanos on 2007-10-10
> **caled said:**
> Would typing df -h in bash not do a better job of displaying drive locations, mount points and available space?

Actually, if you dont have a formatted and mounted partition df -h won't show it, the question is how to list the available hard disks even if they are not formatted. 

Thnk you all for your help :)

---

### Post by Xenaco on 2007-10-10
I don't believe that there are any commands in any operating system or program that will display a list of drive/partitions that are not connected.

You can use GParted to display all disks connected and the partition information.  This will display the disk information, partitioned or not.

---

### Post by nelson.bolanos on 2007-10-10
> **Xenaco said:**
> I don't believe that there are any commands in any operating system or program that will display a list of drive/partitions that are not connected.

You can use GParted to display all disks connected and the partition information.  This will display the disk information, partitioned or not.

:) ... the thread is already solved... thanks for the comment, but just so you know it's not about the disks being disconnected... its about finding out it's identifier :):) connected and all, but not mounted yet, or formatted, just plugged in.

Gparted does my day, thanks.

:popcorn:

---

