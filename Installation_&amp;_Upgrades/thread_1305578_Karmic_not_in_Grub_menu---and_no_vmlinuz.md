---
title: "Karmic not in Grub menu---and no vmlinuz"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Angus77 on 2009-10-30
I've done this twice now, and got the same problem both times.  After installing Karmic, I get the Grub2 menu, which lists Debian and Jaunty (and all the kernels I have installed for Jaunty), but NO KARMIC!

I can boot into Debian and Jaunty fine.  Everything seems fine on the Karmic partition, except I can't make heads or tails of the new /boot/grub folder.

Oh, and there's no vmlinuz in /boot.

Here's how my partitions are laid out.

/dev/sda1 Debian 5.0
/dev/sda2 Karmic
/dev/sda3 Jaunty
/dev/sda5 Home
/dev/sda6 random partition for fiddling around with

---

### Post by Angus77 on 2009-10-30
bump

---

### Post by Angus77 on 2009-10-31
This is infuriating!  I've just tried the same thing with the i386 .iso---I installed via USB, and then again from a spare partition on the harddrive, and both times the system seems to install without a hitch---but Karmic won't show up in the GRUB2 menu, and there's no vmlinuz in the /boot directory!!!

I've been using Ubuntu on two desktops since Feisty, and on my EeePC sinceGutsy, and have never had anything like this problem before.

Am I really alone here?!?

---

### Post by Angus77 on 2009-10-31
Well, I "solved" the problem by downloading the kernel package, opening it up, cp-ing vmlinuz into the /boot directory, and rebooting.  It appears to work (I'm typing from Karmic now) but it sure doesn't make me feel good.

I mean, package managers are there for a reason, right?  Manually sticking the *kernel* into the /boot directory doesn't sound to me like the healthiest thing to do!

Now I'm worried about sticking Karmic on my EeePC...

---

