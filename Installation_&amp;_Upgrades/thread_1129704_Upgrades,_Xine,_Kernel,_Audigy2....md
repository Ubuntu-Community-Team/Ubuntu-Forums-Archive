---
title: "Upgrades, Xine, Kernel, Audigy2..."
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by Johnius on 2009-04-19
I have encountered several problems with my Audigy 2.  Reading the forums, this is not uncommon.  Ubuntu 8.10 ran it fantastically when I first installed.  Every time something upgrades, it either completely eradicates my sound card, or makes it more or less worthless.

First, the solution I found when the kernel updated:  

sudo nano /boot/grub/menu.lst

I rolled the version in the grub back to the CD version by editing the first uncommented line to "default 2".  Problem fixed.

Next, I updated things (as I always do), and believe that Xine updated.  When it did, I lost all command of my Amarok sound (yes, I use KDE in a GNOME environment).  Last week, I could control the individual speakers (5.1 setup) with ALSA.  Now, I only have Front Right and Left control.  The other speakers (center, R and L surround) do not function with Amarok.

I'd roll back the version of Xine too, but I don't know how.  I'd just like updates not to break things.  My guess is that this is a problem with the Amarok xine plugin, not anything else.  But the OSS plugin doesn't work either.

Is it possible to un-update my xine?  Or do I have to wait until Amarok updates the plugin?

---

### Post by Johnius on 2009-04-26
Yes, I'm a horrible person for bumping my own post a week later, but I'm guessing the only solution to this problem is to drop my Ubuntu 8.10 CD back in the drive and start all over... then never update anything again.

---

