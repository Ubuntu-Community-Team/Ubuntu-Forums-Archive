---
title: "Advice for removing Ubuntu"
date: 2011-05-29
forum: Hardware
---

### Post by TScorpZ on 2011-05-29
Hi,

I recently installed Ubuntu on my LG R590 laptop, and I wish to get back to my Windows 7 Home installation. I came across a few links, and I'm not sure which website's advice I should follow 

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927) (pre 4/21/2007 )
or
[http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804) (Last review 2007 zomg)
or
if anyone could give me instructions on how to restore my Windows installation so I can rush my projects I'd really appreciate it!

Here's the information from Disk Utility: ( 640GB hard disk)

/dev/sda1 - 628GB, Unknown (This was the partition that had Windows on it beforehand)
/dev/sda2- Extended partition, 13GB (I limited installing Linux to only 13GB)

Beforehand I made a mistake installing Ubuntu twice cause the first installation just hanged. But using Disk Utility I deleted the first installation. Hence now I have one Ubuntu installation and two swap spaces.

/dev/sda5 - 7MB , swap space
/dev/sda8 - 4.7GB, Linux filesystem
/dev/sda9 - 271MB swap space

Unallocated space of 7.7GB

So if you could help me by giving advice in any way, I'd really appreciate it ! Thanks!
--
On a last note, I really want to come back to Linux. I really do. But it's a pity, getting technical help from my school for software and stuff is like getting a cow to lay an egg. 

I just kinda decided for now that, I need to get **** done, and I needed to get it done yesterday (crazy assignment deadlines and stuff). Call me lazy for not venturing to fix problems like networking and device drivers and not stepping out of my comfort zone. But my laptop's a part of my daily life and I simply depend on it for schooling purposes.

Once again, thanks for reading this

---

### Post by Thewhistlingwind on 2011-05-29
Do you have media for reinstall?

---

### Post by TScorpZ on 2011-05-29
If I understand your question correctly, yes I do have an Ubuntu LiveCD, as well as my Windows 7 installation disk :)

---

### Post by kn0w-b1nary on 2011-05-29
Load up the windows disk, and use their utility to wipe everything and do a clean install.

When you decide to come back to ubuntu, load it in a VM (I recommend VirtualBox) or you can use WUBI, or just a clean Ubuntu install.

Hope this helps!

---

### Post by TScorpZ on 2011-06-01
hey all,

anyway I managed to simply just convert my partition to ntfs, then...simply ran the windows boot disk, installed windows onto that ntfs partition, and then when it was all done all I did was reformat the previous linux partitions... and that was it.

Thanks for reading this. I'll closed this topic if I can

---

