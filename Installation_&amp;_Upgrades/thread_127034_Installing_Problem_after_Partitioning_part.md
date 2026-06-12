---
title: "Installing Problem after Partitioning part"
date: 2006-02-08
forum: Installation &amp; Upgrades
---

### Post by z|x on 2006-02-08
I currently have Windows XP installed on 1 of 4 partitions. I want to be able to choose between Windows or Ubuntu for booting. But I'm not sure what I am supposed to do when they ask me to do the partition setup.
Should I Install Ubuntu with it booting from the same partition as windows or should I set it to boot from a Different partition.

I'm having another problem after selecting the partition that I want to use. I get an error about No root or something like that.

Plss help.

Thanks

---

### Post by yabbadabbadont on 2006-02-08
Here is a guide on installing Ubuntu.

[https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)

EDIT: Actuall, after reading through that, it doesn't really help much.  I just used vmware to simulate what you are doing.  What you want to do is to install ubuntu onto one of the empty partitions.  YOU DO NOT want to install it onto your XP partition as it will destroy the current contents of that partition.  If you are not using the three partitions that don't have XP on them, that is, they aren't formatted or if they are, they don't contain any data that you want to save, then you should take the option to manually edit the partition table and delete the three extra partitions.  MAKE SURE you don't touch your XP partition.  Also, only delete the other three partitions if they currently don't contain anything that you want to save.  Once you have removed the three extra partitions, you sould be able to take the "Guided Partitioning" option.  It should let you select the free space you just created, and then it should split it up for you automatically and you should be able to continue.  I hope this makes sense.  If not, ask more questions and someone here should be able to help you.

---

### Post by z|x on 2006-02-08
Here's what I did. I had 1 partition that I didn't need. It was about 4 GB. So using the disk manager in Windows XP, I deleted the partition. So while installing ubuntu I'll make a new partition from the 4 GB use that. 

I'm still not sure about what I'm supposed to do with the 2nd problem:

> 
I'm having another problem after selecting the partition that I want to use. I get an error about No root or something like that.

---

### Post by z|x on 2006-02-08
Ok, after what I did, it seemed to work. I installed Ubuntu without any problems.

Thanks for the Help!! :D

---

### Post by z|x on 2006-02-08
And now another problem. I can't seem to get connected thru Dial-Up.

See: [http://ubuntuforums.org/showthread.php?p=715064](http://ubuntuforums.org/showthread.php?p=715064)

---

