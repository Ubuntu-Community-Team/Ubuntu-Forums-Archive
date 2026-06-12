---
title: "Problem installing from disc"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by kaazoom on 2009-10-13
Hi,

 I had a massive problem with vista and foolishly wrote over it with ubuntu . ubuntu kept on freezing so I tried reinstalling, which I managed ok but still had the same problem of everything freezing up. I then had to shut it down by turning the power off. I then got a message about it not having shutdown properly, and was told to run fsck (?). I did this. But now I can not install ubutu. If I try turning my pc on without the CD I get a error 13 message from grub.

The CD runs fine as a live disc, but it won't write to my hard drive. It gets to the part where the partition is being configured, goes to 5% and then freezes. Is there any way around this? At the moment I can only run my computer via the live CD. I have run a check on the CD and all seems ok. Any suggestions would be appreciated. I have next to no knowledge of programming.

Paul

---

### Post by bruno9779 on 2009-10-13
You can access Gparted from the live CD's Desktop

you should see it in System > Administration > Partition Editor

there you can organize your partition table (remember swap) and format in ext3 (ext4).

After doing this reboot and choose install.

When you get to the partitioning, choose the ext3 (or ext4) partition you prepared for ubuntu and install there without re-formatting

hope this helps

PS: remember that Gparted can work only on unmounted partitions, so it is always good to run it from the live CD. Also when your Ubuntu is up and running and you just need to re-size.
There are a lot of recovery commands that can be run from a live CD, so it is good to always have one at hand

---

### Post by kaazoom on 2009-10-13
Thank you *bruno9779*[I][I],

 I have been running Gparted for about 2 hours. It seems to be working[/I][/I]*[I], the bar is going back and forth*[/I][I][I], but it is taking a very long time. I have 149 GB to format which id probably the reason. I'll let you know how it goes. Sorry for my ignorance, but what does 'unmounted' mean?

 Paul
[/I][/I]

---

### Post by tpjk on 2009-10-13
> **kaazoom said:**
> Thank you *bruno9779*[I][I],

 I have been running Gparted for about 2 hours. It seems to be working[/I][/I]*[I], the bar is going back and forth*[/I][I][I], but it is taking a very long time. I have 149 GB to format which id probably the reason. I'll let you know how it goes. Sorry for my ignorance, but what does 'unmounted' mean?

 Paul
[/I][/I]

a partition that is 'unmounted' is not 'part of the system' (so to speak); that is, it's not in use and therefore can't be accessed. if you want to write to a partition and/or read/execute files that are on that partition it has to be mounted/made accessible. at the same time, if you want make changes to the partition itself (e.g. resize or move it), you can only do so if it is not mounted.

---

