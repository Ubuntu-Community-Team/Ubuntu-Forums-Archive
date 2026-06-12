---
title: "Using Grub2 for multiboot and Ubuntu install on external USB HD"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by gd1107 on 2009-08-12
I'm trying to make my WD passport drive a multiboot system and run a "live" ubuntu distro that I can take anywhere.

What I did so far was remove my internal HD and installed Ubuntu 9.04 to my external drive.  I then updated to Grub2 after testing it.  Everything was working great until I put back in the internal drive.  

On booting into Grub, the external drive is hd0. After loading into Ubuntu, the external drive becomes hd1.  This is causing some weird permission errors with gnome (doesn't see my home folder to start with) - I can only get to fail safe terminal.  Also, when I run update-grub after booting into Ubuntu, the output file /boot/grub/grub.cfg is showing the root as hd1, so upon reboot, I have to manually edit the boot menu to get back into ubuntu.

any ideas of what I can do to remedy this?

---

### Post by e.m.fields on 2009-12-23
Hey. 
I'm no expert in this area, but it's something I've considered doing myself.
I gather that you can have GRUB identify the various drives by their location name (ie hda1 or whatever) or their UUID. While the location may change depending on how many drives you have connected, the UUID should never change.  I *believe* that you can find the UUID of this external drive, and tell grub to boot from there, regardless of where it is.

Please let me know if this helps you so I'll know for myself.

---

