---
title: "Triple boot, Vista, W7 &amp; Ubuntu 8.10 in a RAID 0 array, ICH10R (fakeraid?)"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by mcastaneda68 on 2009-02-03
I have a RAID 0 array with my onboard SATA controller.

The RAID0 array is made from 2x250 GB Seagate HDDs, which make a 500GB Volume. I have a separate 500GB HDD for my data.

Using the Vista installation disk, I created partitions as follows:

 - one for Vista Ultimate x64, 300 GB
 - one for the Windows 7 beta, 100 GB
 - Left the remaining as "free" space for Ubuntu 8.10

I have now installed Windows Vista & Windows 7, but when I try to install Ubuntu, it does not recognize the RAID array. Instead, when the partitioned starts, I can see both 250 disks, independent and not in a RAID array.

I understand these RAID controllers are called fakeRAID's but, is there a way I can make Ubuntu recognize the array so I can install Ubuntu 8.10 on it?

I tried Gparted, but I got the same thing.

Thanks in advance,

---

### Post by mcastaneda68 on 2009-02-04
I found this [article]("http://www.howtoforge.com/creating-a-dual-boot-system-on-raid10-ubuntu-windows") when googling for an answer.

Will this work?

---

### Post by mcastaneda68 on 2009-02-20
Just wanted to leave a record on how I did it:

- Created RAID0 using the onboard RAID BIOS
- Created 2 NTFS partitions for Vista & Windows 7 using Windows boot DVD. Left the xtra room for Lunix partitions
- Installed Vista
- Installed Windows 7
- Installed Ubuntu, using the alternate install disk, which has the dmraid required for it to recognize the fakeraid

Hope it helps anybody else looking for this kind of answer...

---

### Post by gilson585 on 2010-01-07
Try a newer version like 9.10 *dmraid* has come a long way since 8.10 and is much easier to get running. You no longer need the alt cd and can install using the live cd. Although I must say I've heard the ICH10R is kinda touch and go under Ubuntu. I have seen it work for some and not others. Particularly when the array has been rebuilt there have been issues installing as the metadata becomes somewhat invaild. Aside from that it will install but fails to boot using GRUB2 and you need to revert to GRUB legacy [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445) . There have been rumors this will be fixed in 10.4 making the implementation of *dmraid* work with GRUB2. Hope this helps you.

---

