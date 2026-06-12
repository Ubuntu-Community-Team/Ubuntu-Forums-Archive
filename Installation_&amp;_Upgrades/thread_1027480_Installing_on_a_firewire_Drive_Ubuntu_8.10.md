---
title: "Installing on a firewire Drive Ubuntu 8.10"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by Chipmunkzors on 2009-01-01
Hey, I've searched the internet about this with mixed results. Some show long drawn out processes which I just can't follow and some aren't relevant to my set-up.

So how would I go from my CD to installing it on a firewire drive. I read somewhere if you unplug your hard drive then boot from the disk into live then install that works but I don't fancy playing about unplugging things. Any alternative easy ways to install onto a firewire drive which I then will be able to boot from.

This is a shared computer so the windows installation on the internal drive must be preserved and only booted into when the firewire is plugged in. (This is possible right?)

I have a little experience with Ubuntu before and want to experiment with it again.

Thanks Guys

edit: Also I seem to remember having to partition two drives one for system files or something and another for other stuff. What's the split of file size? 80%/20%?

---

### Post by ChronoSphere on 2009-01-01
It is possible without unplugging anything.

First, make sure your PC can boot from an external drive. You probably have to change the boot order in the BIOS, or press a key (F12 or something) during boot up to select another boot drive.

Then, plug in the firewire drive, start the installation and install to the external drive while leaving the internal untouched. You can use one partition for system and data. Make sure you install GRUB to the MBR of the external drive. Don't install anything on the internal drive or modify it in any way and you should be all set.

Now with the external drive unplugged, you'll boot like before. And when it is attached you'll boot into Ubuntu.

---

