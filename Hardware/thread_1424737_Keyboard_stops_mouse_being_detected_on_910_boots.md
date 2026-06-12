---
title: "Keyboard stops mouse being detected on 9/10 boots"
date: 2010-03-08
forum: Hardware
---

### Post by evilearthwormjim on 2010-03-08
Hi there,

I'm pretty much brand new to Linux and have a quirky problem.

I've installed Ubuntu Remix onto my eeepc 901.

Everything is working except for one small hardware problem. My keyboard got slightly damp a while back and as a result my Tab key fires randomly as if being pressed. 
While under Windows, I just remapped the tab key to caps_lock and disbabled the original tab key, problem solved. I can do the same in Ubuntu using xmodmap. The problem is that the faulty keyboard stops the touchpad being detected on nearly every boot.

If I take off the keyboard and remove it from the ZIF connector, Ubuntu boots, mouse works and then I can plug back in the keyboard and everythings gravy.

So is there a way that I can:

A) Disable the keyboard being detected on boot, or
B) Disable the Tab key before the trying to detect the mouse, or
C) Will I just have to bit the bullet and order a new keyboard (this is option C as A and B are free)

I've tried adding pci=noapci and i8024.nokrb to the /etc/default/grub file (and then running update-grub) with no joy.

I'd be interested to know if this can be done? Thanks in advance.

---

