---
title: "How to Partition Hardware RAID 0?"
date: 2010-05-02
forum: Hardware
---

### Post by killercoderninja on 2010-05-02
I have recently created a new RAID 0 array out of two 500gb hard drives. I  enabled RAID in my BIOS, configured the array, then installed ubuntu  10.04 on the array. Everything went smoothly, and I am very pleased with  the increased performance.

However, I would like to dual boot with Windows 7. I cannot figure out  how to partition my array! GParted just sees /dev/sda and /dev/sdb as  two unformatted 500gb drives, even though the ubuntu file manager sees  only my 1Tb file system.

How do I partition my RAID array?

Thanks in advance!

P.S. I am aware that RAID 0 is dangerous, has no fault tolerance, and is  more likely to fail.

---

### Post by killercoderninja on 2010-05-02
This is on an Intel ICH10R controller on a Gigabyte EP45-UD3R motherboard, if that helps.

This is particularly frustrating as the Ubuntu and Windows installers both see the RAID array instead of the independent disks. However, neither of these tools allow me to shrink a partition and add a new one; only delete or reformat.

---

### Post by leopardb on 2010-05-03
What you have is not *real* hardware raid. 

Look at this thread for more info :

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

As for dual booting on it, though i don't even know if it's possible, i think it's really going to be a long road, but good luck anyway...

And i guess you shouldn't double post :)

---

