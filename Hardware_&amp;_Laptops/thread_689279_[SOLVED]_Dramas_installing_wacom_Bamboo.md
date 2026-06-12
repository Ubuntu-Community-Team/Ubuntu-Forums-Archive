---
title: "[SOLVED] Dramas installing wacom Bamboo"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by Robynsveil on 2008-02-06
First off, I have read and followed every thread on this forum on the subject, and inevitably bogged down at some stage. First I followed [this thread]("http://ubuntuforums.org/showthread.php?t=631881&highlight=Wacom+Bamboo"), and then I followed [another thread]("http://ubuntuforums.org/showthread.php?p=3728548#post3728548") which conflicted somewhat with the first one. Finally, I found[ this thread]("http://http://ubuntuforums.org/showthread.php?t=687746&highlight=Wacom+Bamboo+NVidia") where I once again carefully followed the instructions, but ran hard aground at Step 8 of the [recommended tutorial]("http://ubuntuforums.org/showpost.php?p=4014004&postcount=32")... turns out it was focused on the Bamboo Fun, whilst I have just the Bamboo. The author of the tutorial recommended to go to the [updated version of his tutorial]("http://ubuntuforums.org/showpost.php?p=4253232&postcount=133") which I did and promptly ran aground at the same step: 8.
So it is with some frustration and desperation that I finally have no choice but to create a new thread.

In summary, what I do is the following in terminal, logged in as me, not root or su:
1._ uname -r_     .....     which gives me: **2.6.22-14-386**

2._ lsusb | grep -i wacom_   .....   which gives me: **Bus 001 Device 003: ID 056a:0065 Wacom Co., Ltd **

3.make the wacom folder and cd into it

4.sudo apt-get install build-essential x11proto-core-dev libxau-dev libxdmcp-dev x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-xext-dev libxext-dev libxi-dev linux-libc-dev libc6-dev libncurses5-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev
...which gives me...
**[this]("http://www.tightbytes.com/Stuff/Install_devs.txt")**

5.Download and untar 'cd linuxwacom-0.7.9-7/', then go into that folder

6.Here's where we run into our first conflicting advice. This guru said:
> ./configure --enable-wacom

where another advised against the " --enable-wacom" argument. In any event, the output at the end was **[this]("http://www.tightbytes.com/Stuff/Configure_Enable_Wacom.txt")**. So, I've got wacom.o built. Or ready to build, anyway. Issued a make which produced **[this]("http://www.tightbytes.com/Stuff/Make_Wacom.txt")** and then the "sudo make install" produced **[this]("http://www.tightbytes.com/Stuff/Sudo_Make_Install_Wacom.txt")**.

7.Did this:
> 
cd ..
cp /etc/X11/xorg.conf .
gksudo gedit /etc/X11/xorg.conf


and here was the **[xorg.conf]("http://www.tightbytes.com/Stuff/Xorg_dot_conf.txt")** this produced. Thought I'd have a quick look in the /dev/input folder: there is no wacom folder or file. Might there be an issue here?
Anyway, I did all the find and replace tasks, then 
> cp /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko .
and 
> sudo cp linuxwacom-0.7.9-7/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko
gave me no back-chat, nor did:
> sudo depmod -e
...so I should assume that I've got an installed tablet. I don't. I've got [IMG]http://www.tightbytes.com/images/ubuntu/NoWacom.jpg[/IMG]

...so, what am I missing?

Thanks to all who respond!

---

### Post by Robynsveil on 2008-02-07
Got it working -- see[ this thread]("http://ubuntuforums.org/showthread.php?t=631881&page=16")... :KS

---

