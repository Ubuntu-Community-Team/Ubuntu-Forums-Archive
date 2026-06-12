---
title: "Poor workaround for displaying ubuntu on Samsung television"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by Tdonohue on 2007-07-14
I have been trying to display feisty on my Samsung HDTV. It is connected via VGA->component on my Ati X1650 pro.    I was able to do the install no problem, but on reboot, and any other boot since, I get strange lines and bandings (white and green) on the screen, no desktop.  Connected to a regular monitor, it works just fine.

One day the PC, in Vista, rebooted overnight and booted into feisty.  when I turned the tv on in the morning, it was displaying my feisty desktop.  So I've tried letting it sit for a while, but I don't want to ruin my tv.

I've discovered one workaround.  Boot into recovery mode, startx, then once in x, open a terminal and type 'GDM'.  Then it works fine, but  800x600 is the highest resolution.  I can't get the proprietary ATI driver to work, because, once it is enabled, the original problem  remains, but my workaround won't work.  I have to reconfigure xorg, then do my workaround.


Any help on how to resolve the issue so I can simply boot into Feisty?  Your help is always appreciated!

Tim

---

### Post by Tdonohue on 2007-07-19
Any ideas out there...

---

