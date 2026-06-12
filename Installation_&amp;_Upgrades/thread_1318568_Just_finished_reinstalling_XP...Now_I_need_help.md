---
title: "Just finished reinstalling XP...Now I need help"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by macruadhi on 2009-11-07
To begin, I have a Dell Inspiron 530, 1 gb ram, 145 gb hd, 500 gb hd. Windows Xp home, and Karmic.




Yesterday I installed Xp, then Karmic. I let Ubuntu choose all my settings, it divided HDD 1 into equal parts and installed Karmic on partition 2, installed bootloader, etc. After the ubuntu install I was unable to boot Xp. I searched the forums, but never found a situation quite like mine. I could boot into Karmic, but when I tried to boot Xp it just stared at me with a single blinking cursor and no ability to give it input. I tried amending /etc/grub.d custom file, with no success. 

So I have just reinstalled Xp and really want a working dual boot system. I am leaning toward a Wubi install,(which has worked fine in the past.) but I would like to be able to access all disks and their partitions, something I can't do with Wubi.

Does anyone have any pointers?

---

### Post by Yvan300 on 2009-11-07
What to do is make sure to partition your drives before installing xp, that way partitioning won't damage it. Also you may want to try easybcd as your bootloader instead of grub.

---

### Post by xian.r on 2009-11-07
Usually when I set up a dual-boot system I always defrag the windows partition before the ubuntu install, even if the windows install is a fresh install.  Especially if you are re-sizing the windows partition.

I also chose to do the partitioning manually, during the ubuntu install, so that I know exactly how the partitions are being set up.  

For ubuntu I set up two partitions:
[LIST]
[*]Swap space (double the size of your RAM, e.g. 2GB of RAM == 4GB swap space)
[*]the OS partition (I fill up the rest of the disk with this)
[/LIST]

Hope this is helpful.

---

### Post by stlsaint on 2009-11-07
> **Yvan300 said:**
> What to do is make sure to partition your drives before installing xp, that way partitioning won't damage it. Also you may want to try easybcd as your bootloader instead of grub.

why may i ask would the user use easybcd(truly made for windows) over built in bootloader for ubuntu?


> So I have just reinstalled Xp and really want a working dual boot system. I am leaning toward a Wubi install,(which has worked fine in the past.) but I would like to be able to access all disks and their partitions, something I can't do with Wubi.

All you need to do is re-install grub2. 
see [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202").

also if you want to dualboot do not let ubuntu choose the partitions itself, you configure parititons manually, please see signature for help.

---

