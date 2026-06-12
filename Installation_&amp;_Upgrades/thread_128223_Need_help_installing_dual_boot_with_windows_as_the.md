---
title: "Need help installing dual boot with windows as the primary OS"
date: 2006-02-11
forum: Installation &amp; Upgrades
---

### Post by Ltgeo on 2006-02-11
Hey guys,

I have a problem and I was wondering if anybody would be able to help. I'm not completely new to linux but I still don't understand the complexities.

What I was wondering is how can I install Ubuntu to dual boot with XP while keeping XP as the primary OS. 

Previously I have had Ubuntu and Xp installed however Ubuntu was the primary OS. I had 2 physical hard drives, the main one with Ubuntu and the other with XP. When I booted the computer GRUB prompted me to select which OS to run, however if I didnt select any within a certain time then Ubuntu would load by default. Is there a way to reverse this and use the windows XP mbr so that Windows is the default?

I haven't tried anything as of yet because this computer is brand new. So I'm hesitant to mess with anything because I already have a SATA 250gb hard drive with XP Pro installed and I'm not in the mood to lose the hours of hard work it took to get my system how I want it. What I would like to do is add a secondary IDE drive from my older computer and use this to install Ubuntu. Is it going to be possible to do this in a dual boot with Windows as the primary OS?  :confused: 

Any help would be greatly appreciated.

---

### Post by jpkotta on 2006-02-11
It's easy to set which OS to boot if you know where to look.  Edit /boot/menu.lst.  Find the line with ```
default 0
``` and change it so that it points to the Windows entry.  The entries are numbered from 0 to N-1.  Alternatively, move the Windows entry so that it is the first one.  When you're done, do ```
sudo update-grub
```

You may have to edit menu.lst a bit more for two separate HDDs, but it's not too bad.  And don't worry about having to reinstall either OS if you screw up your bootloader.  As long as you have a Windows install CD and/or a Linux live CD, you can almost always fix things without a reinstall.

---

