---
title: "Format blank hard drive so I can set it first in boot order, or just install now?"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by rainwalker on 2009-06-10
I'm trying to install Ubuntu on one of my computer's two hard drives, the other one already has Vista on it. I was told to set the other (blank) hard drive first in the boot order and install both Ubuntu and GRUB to it so that GRUB would give me a choice of what OS to boot into at startup, but my BIOS won't let me move the unformatted drive in the boot sequence; it's stuck under "Excluded from boot order".
Should I go in with Gparted or something and format the drive? Or should I risk installing Ubuntu onto it and then moving the drive to be first in the boot order at the next boot? My aim is to install GRUB on that same drive so that it runs before Vista boots, giving me a choice of what OS to run.
Help?

---

### Post by presence1960 on 2009-06-10
I would use the Ubuntu Live CD or gparted Live CD to create my partition(s) on the unformatted drive. Then install from the Ubuntu Live CD using the "manual" option at the Prepare Disk space window of the partitioner.

You will then probably be able to move that new disk to first boot in boot order in BIOS.

---

