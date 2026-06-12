---
title: "kernelpanic on wakeup -&gt; ubuntu not booting anymore, sda not showing in gparted"
date: 2011-06-11
forum: Hardware
---

### Post by Runoratsu on 2011-06-11
Heya everybody,

A short while ago I finally installed ubuntu 11.04 on my old EeePC 901 Go, since EB4 beta, which I had installed previously, hadn't been updated for such a long time…

Anyways, I guess the problem isn't even really related to the Ubuntu install.

A few days ago on the way home from work I put the computer into suspend, as always, and when I wanted to wake it up again, it showed a kernel panic. Okay, this can happen, no need to worry, I thought. So I rebooted, but after the boot menu where I can choose if I want to boot into Ubuntu, it's recovery mode or whatelse, it  displayed an error of not finding the kernel or something along those lines.

I then installed a live ubuntu onto a 4gb SD card and used that for the remainder of the week since it's so crazy at work atm that I just didn't find the time to do anything about the problem until today.

Well, here I am.
____________________

Disk Utility shows the 901's SSD, and displays it as having 4 Partitions, but says "unknown scheme", gparted doesn't display sda at all, only the sdb SD-Card, as does testdisk. 

On the evening the crash happened I ran "boot-info-script", I'll attach its output.


I'd be really grateful if somebody would tell me how to proceed. The data on sda is not really important, but still, I'd be happy if the last days' bookmarks, chat logs, etc, wouldn't be lost.

Even after 3 years or so of using linux on the little Eee I'm still pretty much a linux noob, so it would be nice if you could write your tips so that even one with only very shallow linux knowledge like me understands them ;)

Thanks in advance!

Johann

PS: Ubuntu rocks! It looks sooo polished in its current iteration! No comparison to eeebuntu/EB4 beta! I love it. (although I boot into Ubuntu classic without Unity for performance reasons)

---

### Post by dabl on 2011-06-11
It looks like the partition on /dev/sda is hosed. If there is important data on it, then you might try something like Ultimate Boot CD:  [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

If you can live without whatever is on it, then I would start by making a new partition table, then a new partition and filesystem.  Personally I like my Parted Magic USB stick for such adventures:  [http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)

but it is a fact that gparted is all you actually need just to make the partition table and the partition.

---

