---
title: "Very strange problem regarding wubi, ubuntu, and topologilinux"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by peel on 2009-03-31
Hello all.

For the past few days I have been somewhat obsessed about trying out a Linux distribution. I am currently running Vista and I would like to continue running Vista and I do not want to lose anything on their. However, I would like to dual boot with Ubuntu, or maybe some other system.

In any case, I started with trying to install Topologilinux, which didn't quite work. I got most of the way through the download, and then it stopped, so I for some dumb reason tried to install it without a CD. Obviously, it did not work out, but what did happen was when I rebooted I could choose between Topologilinux 7.1 or Vista, and when I clicked Topologilinux it said there was an error. I tried Topologilinux 6.1, as that took less time to download and it didn't work outside of colinux, so I deleted it.

I then found out about installing Ubuntu through Wubi. I figured this would be the best option for me, so I downloaded the two of them. Wubi seemed to be working well, everything seemed to be successful, but when I rebooted my computer and went down to Ubuntu (although Topologilinux was still there), The options that came up where something along the lines of:

run Topologilinux 256 1024x1280
run Topologilinux
run topologilinux cmdr
run topologilinux cmdd
use topologilinux for installation.
return to previous screen

It wasn't exactly that, but something like it. I tried clicking each of them, and none of them worked. I tried going back and deleting every trace of Topologilinux I could find, but still the same problem showed up. I tried uninstalling and reinstalling Ubuntu through Wubi many times, and the same problem came up every time. I have no idea how to fix this. It would be nice if I could also remove my Topologilinux boot option, since Topologilinux is no longer on my computer at all...

But if any of you have any advice to offer whatsoever, it would be greatly appreciated.

---

### Post by cariboo on 2009-03-31
Probably the easiest way for you for you to ge rid of the Topologilinux in the grub menu is to remove them from /boot/grub/menu.lst. To do this, when at the Ubuntu desktop, press Alt-F2 and type:

```
gksu gedit /boot/grub/menu.lst
```

The above command opens the Text Editor as root and allows you to edit a file that you don't have permissions to. Just remove any reference to Topologilinux.

Jim

---

### Post by peel on 2009-03-31
Thank you, but I am unable to get into my Ubuntu desktop in the first place. I am stuck with Vista.

---

### Post by peel on 2009-03-31
I have installed VistaBootPro. Looking at my BCD registry settings, I noticed that the following was present:


Real-mode Boot Sector
---------------------
identifier              {03e20275-18f9-11de-a1d3-0007e96e29bd}
device                  boot
path                    \grldr.mbr
description             Topologilinux 7.0.1

Real-mode Boot Sector
---------------------
identifier              {03e20277-18f9-11de-a1d3-0007e96e29bd}
device                  partition=C:
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu


I don't know much about this, but I am guessing that this information could be helpful. This is after I uninstalled Wubi.

---

### Post by peel on 2009-04-01
I have installed Ubuntu on my notebook and it's working fine, except my desktop still has the same problem.

I even reinstalled vista on my desktop, and the same problem occurs. I have no idea how to fix my boot menu.

---

