---
title: "three different machines: grub setup fails on all of them"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by ljwobker on 2009-01-09
I've been messing around with a couple of different servers at work and a home machine that I'm planning on turning into a NAS box, and have noticed that on all three installs, grub has not been set up correctly (fails on loading stage 1.5).  Doing a little bit (well, ok, a LOT) of reading has gotten me to where I can fire up a liveCD on my USB key, run grub from there, find the correct stage1.5/stage2 files, "setup" the correct hard drives, and happily move on...

but what I can't understand is why the installs (using the standard ubuntu 8.10 server install CD) didn't work in the first place.  everything else about the system install went fine, only the grub part got wacky.  I can't figure out anything specific to the machines that would cause this, either... two of them were installed from CD, one from a USB key (shouldn't matter).. All use SATA drives, the two work servers are older 1RU AMD units with hotswap bays and the home machine is just a regular intel home-build.  

Just to be sure there weren't issue from some previous install, I did a full wipe of ALL drives in each system via **[FONT=Courier New]dd if=/dev/zero of=/dev/whatever bs=1M count=1[/FONT]** -- if that won't clear out any old cruft I don't know what will.


Even though it was pretty easy to fix, it definitely required a lot of sleuthing around the forums and several hours of banging away... and ultimately I would like to both:
1) save others from possibly hitting the same problem...
2) understand for my own education exactly what happened vs. what SHOULD have happened.

At this point the two work servers are up and running so I can't really mess with them, but if anyone is willing to help track this down I can whack the home machine and try reinstalling one more time.

thanks!

---

### Post by ljwobker on 2009-01-11
Bump.  I also tried booting from a USB stick that I'd copied the CDROM to -- the install worked (Again) except for the grub part (Again) -- I had to boot the liveCD and run grub manually.  again, it's not that big a deal for me (once I figured out how) but it seems like the installer ought not to mess this up.  :(

---

