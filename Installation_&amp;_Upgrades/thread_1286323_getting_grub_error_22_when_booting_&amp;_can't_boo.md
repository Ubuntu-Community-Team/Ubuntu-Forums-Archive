---
title: "getting grub error 22 when booting &amp; can't boot at all"
date: 2009-10-08
forum: Installation &amp; Upgrades
---

### Post by tRiBaLmArKiNgS on 2009-10-08
I'm new to Ubuntu and dual boot installed with windows 7 no problems. I forgot to move the slider to the desired disk space amount for ubuntu though, and ended up messing with my partitions to try to get more volume for Ubuntu.... I don't know what I've done but when I boot now I get grub error 22 and cant get onto windows or ubuntu!

I need some serious help

---

### Post by SkyNet2029 on 2009-10-08
Hi. A Grub error code of 22 means Grub is looking for a partition (listed in the partition table) that is no longer there. 
A simple way around this would be to reinstall Ubuntu, paying attention to specifying the partition for Ubuntu. This will also reinstall Grub, allowing you to boot into windows 7 or Ubuntu.
This works because Windows 7 is still on the disk, and while installing Ubuntu, the installer will search for any existing operating systems (windows 7) and add them to the Grub boot list.
Hope this helps.

---

### Post by tRiBaLmArKiNgS on 2009-10-11
> **SkyNet2029 said:**
> Hi. A Grub error code of 22 means Grub is looking for a partition (listed in the partition table) that is no longer there. 
A simple way around this would be to reinstall Ubuntu, paying attention to specifying the partition for Ubuntu. This will also reinstall Grub, allowing you to boot into windows 7 or Ubuntu.
This works because Windows 7 is still on the disk, and while installing Ubuntu, the installer will search for any existing operating systems (windows 7) and add them to the Grub boot list.
Hope this helps.

Thanks for the help :D

---

