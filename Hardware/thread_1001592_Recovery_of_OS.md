---
title: "Recovery of OS"
date: 2008-12-04
forum: Hardware
---

### Post by mayureshupadhye on 2008-12-04
Hello Everyone!
I have been using Ubuntu linux for quite some time now, but this is my first post in this forum.

First of all I would like to thank canonical and ubuntu for providing the free cd.

I use dual boot with windows, and my problem is that if I re-install my windows, I lose my ubuntu boot screen, and also if i format my linux partitions, I am unable to boot windows.
how can i fix?
Please help.

---

### Post by gjoellee on 2008-12-04
well you should not try to do a dual boot when you installed Windows at last, or reinstalled Windows. This will causew a lot of problems with GRUB, that you don't want.
 
TIP: Install Windows first then Ubuntu
 
I am not sure how to help you on this one sorry...

---

### Post by caljohnsmith on 2008-12-04
It's OK to install Windows after Ubuntu, but as you found from experience, Windows overwrites Grub in the MBR (Master Boot Record) so that you can't dual boot any more. The solution is usually easy, just boot your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands. Next reboot, and you should have the Grub menu on start up again if all goes well. Let me know how it goes. :)

---

