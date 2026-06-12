---
title: "Unable to install GRUB in (hd0)"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by kaushik_srkr on 2009-07-16
I use ubuntu 9.04 for few days and it is very nice. So I just repartitioned my hard disk and provide 40 GB for ubuntu (previously 20 Gb) and 2 Gb for swap (as RAM is 1 Gb). But after that when I try to install Ubuntu 9.04 after 94% I received an error message as below:

Title: Unable to install GRUB in (hd0)
Message body: Executing 'grub-install (hd0)' failed.
This is a fetal error.

My hard disk partition is as below:

Primary 1 : linux (ext4)
Primary 2 : Swap
Primary 3 : Drive C
Extended : rest of the part
Partition format is just like before when I used Ubuntu comfortably. I just change the size of the drive. Thats all.

---

### Post by csabo2 on 2009-07-16
what did you use to resize the partition? and which way did you grow it? (did you remove a partition before or after the 20GB one to expand it)

---

