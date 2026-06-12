---
title: "Moving Ubuntu to new machine?"
date: 2008-07-25
forum: Hardware
---

### Post by JasonWalton on 2008-07-25
I know this has been covered before, but a quick search through the forums finds a bunch of conflicting answers.

Last night I tried to move my Ubuntu installation to a new hard drive in a new machine.  I copied everything over, and reinstalled grub, got Ubuntu booting fine, but neither the onboard netword card, nor the second network card in the new machine are recognized.  When I boot off the Ubuntu live CD, though, both cards show up fine.

Obviously there's some sort of hardware detection that occurs on the boot CD which doesn't in my case.  Does the boot CD just try to load all the hardware modules in the world, and see if anything sticks, whereas an installation only installs the modules that are actually required?  Is there any way to re-run whatever hardware detection occurs at install time?  Maybe do an lsmod off the boot CD and diff that against an lsmod when booting off the drive?

I know about "sensors-detect", which is a handy way to find hardware sensors, and "sudo dpkg-reconfigure xserver-xorg" for X (although this is a server install, so there is no X to reconfigure).

Is it worth the time and agony trying to get this working, or should I just reinstall Ubuntu?

---

### Post by evets25 on 2008-07-25
Show us your lspci, and perhaps someone might be able to help you. (run "lspci" from commandline and post the results here) 

It's always nice to get to the root of a problem, but perhaps reinstalling ubuntu is your best option here. Besides, it's not like it's hard or anything. I average about 30 minutes per install, including basic post-config, depending on the computer. :)

---

### Post by JasonWalton on 2008-07-25
Ok, turns out this was a lot simpler than I thought it was.

The cards were both found, but since they have different MAC addresses, /lib/udev/write_net_rules was assigning them new eth# IDs, and reserving eth0 and eth1 for my old cards.  I thought I'd done an "ifconfig -a", but evidently not.  :P

Thanks for the help!

Just out of curiosity, how DO these modules get loaded at startup?  If I pick one of these network cards and find the module it's using (with hwinfo, say), and then grep through /etc looking for that module name, I don't find it.  How does this work?

---

