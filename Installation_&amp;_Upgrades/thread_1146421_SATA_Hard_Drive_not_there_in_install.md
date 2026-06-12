---
title: "SATA Hard Drive not there in install?"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by Traygon on 2009-05-02
Hello there guys,

Trying to find some helpful information but utterly failing at the moment, if anyone could point me in the right direction or help me directly that would be awesome :)

What I am trying to achieve is installing Ubuntu 64bit on my desktop, I really need to have Ubuntu in my digital time on the computer or laptop but as many tries on getting it to work on my Fujitsu Seimens Esprimo v5535 so my desktop is the next stage. It is a gaming built machine (I will be using XP in virtual box and see about using Wine or native) running the following spec:

XFX Geforce 6200 AM2 socket
AMD Athlon 64 x2 5000
320GB WD SATAII
HD Radeon 4670

There was a slight problem with the brand new SATA DVD RW not being able to load Ubuntu without that BusyBox to pop up so an old IDE RW is now being used, I get through to the Live environment or through the text alternative installer but when the installer (on each edition) gets to the partitioner, it doesn't detect the hard drive.

All components are brand new (December 08) and were running Vista and XP perfectly fine. Any help would be appreciated :)

Best regards.

---

### Post by Alterax on 2009-05-02
On the alternate cd, before you select the drive (or attempt to), try hitting alt-F3 to get a different terminal.  Activate it and type:

```
modprobe ide-core
```

to add the ide kernel module.

Next, return to the installer with either alt-F7 or alt-F8 (it's one of those two, I do believe alt-F7 though).  If that doesn't work, let me know.

---

### Post by Traygon on 2009-05-03
Hello Alterax,

Thankyou ever so much for your help and post, I typed in 'modprobe ide-core' and it says Module not found. Any other suggestions available?

Best regards.

EDIT: Also, on a side note, only Alt+F1 returns me to the install, software and hardware I use always seems to act differently than others.

---

