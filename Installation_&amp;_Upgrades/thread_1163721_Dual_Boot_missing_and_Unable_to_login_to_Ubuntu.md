---
title: "Dual Boot missing and Unable to login to Ubuntu"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by nlg on 2009-05-19
I installed Ubuntu and XP on 2 partitions on one hard drive. Initially I had dual boot and could successfully use both OS.

But I formated XP and re-installed it. This overwritten the Boot file.

Now I can only access XP but not Ubuntu.

How can modify the Master Boot File using a Ubuntu Live CD. What command do I need to use?

Your help is much appreciated.

Thanks in Advance
Nlg

---

### Post by tommcd on 2009-05-19
You need to reinstall the grub bootloader to the MBR. This will allow you to boot Windows or Ubuntu like it was before you reinstalled Windows:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)

And welcome to the Ubuntu forums!

---

