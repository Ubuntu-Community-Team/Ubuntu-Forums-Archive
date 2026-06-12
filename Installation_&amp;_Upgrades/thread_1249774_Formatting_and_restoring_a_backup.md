---
title: "Formatting and restoring a backup"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by lduperval on 2009-08-25
Hi,

I want to format and restore a backup on a computer. What is the best way to do this, without necessarily downloading a complete distro?

Here is what I want to do:

- resize (vista) partition
- create and format new partitions to support ext3 and swap
- extract .tgz file created with Simple Backup
- install grub
- reboot
- smile because life is good!

Is there a tutorial or something that can help me out for this?

Thanks,

L

---

### Post by louieb on 2009-08-25
Have you looked in the tutorial and tips section? Guess your just looking to put the tar file in the new partition and extract it there. 

I use partimage so not much help with tar but just a guess.

```
tar -xvpfz  /backup.tar /
```
[Heliode: Backup and restore your system! - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=35087&highlight=tar+backup") 
[A-star: Backup and restore your system! - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=81311&highlight=tar+backup") 
[Howto: Backup your PC using "tar" -  Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1019517&highlight=tar+backup") 

The 1st 2 are pretty much the same. The last goes into more detail about tar options. 

And this is how i do it - works great. 
[Howto: Backup with Partimage - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=287522")

---

