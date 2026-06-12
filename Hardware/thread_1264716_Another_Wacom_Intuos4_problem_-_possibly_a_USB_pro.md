---
title: "Another Wacom Intuos4 problem - possibly a USB problem"
date: 2009-09-12
forum: Hardware
---

### Post by smIsle on 2009-09-12
I've been trying to get my new wacom tablet working - with no luck.

I've installed the latest LinuxWacom driver, I've added wacom to my module list ...

the main problem seems to be that my Xserver isn't recognizing when I plug it in.  Other USB devices work, specifically my mouse.

Running dmesg|grep [Ww]acom returns: 

```
[  627.110047] usbcore: registered new interface driver wacom
[  627.110050] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
```

which is missing the last line that most people see.  When I started a few hours ago, nothing at all showed up there.

All of the other tutorials I've found assume that you are past this phase in the troubleshooting (or just say, plug it in and it will work, and nowhere to turn if it doesn't).  I sort of think it's part of a larger problem, but I don't have enough experience with linux to know what.

---

### Post by Favux on 2009-09-12
Hi smIsle,

Welcome to Ubuntu Forums!

When you say:
> I've installed the latest LinuxWacom driver
Do you mean you compiled a new wacom.ko and copied it into place?  Which version?

Just went through something similar with simonced here:  [http://ubuntuforums.org/showthread.php?t=1262674](http://ubuntuforums.org/showthread.php?t=1262674)   Maybe if you skim through it something will pop out at you.

---

### Post by smIsle on 2009-09-12
thanks!

I actually just followed [http://ubuntuforums.org/showpost.php?p=7246549&postcount=63](http://ubuntuforums.org/showpost.php?p=7246549&postcount=63) (written by you, again, thanks!)

and I have it working - just need to work out some configuration kinks.

Earlier, I was trying to install the whole module (as per some other instructions), and it wasn't working at all.

EDIT - newbie question - how do I set a thread to solved?  I saw options like that when i started this thread.

---

### Post by Favux on 2009-09-12
Hi smIsle,

Great!  Good work.

Thread tools at the top.

---

