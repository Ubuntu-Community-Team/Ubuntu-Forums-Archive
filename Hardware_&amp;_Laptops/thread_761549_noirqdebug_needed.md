---
title: "noirqdebug needed"
date: 2008-04-21
forum: Hardware &amp; Laptops
---

### Post by squarooticus on 2008-04-21
The IRQ debugging code in the kernel is probably great for developers' and power users' finding bugs, but is counterproductive for use of Linux by all but the most knowledgeable.

I reinstalled Hardy from the beta ISO yesterday because I was having problems with gnome and didn't feel like messing around with packages trying to solve it.  (Rest assured this is not something a typical user would run into, though I would recommend an easy way to "delete all desktop settings and start over" short of deleting the entire home directory; it took me a while to find the stuff under .config.)  But when I reinstalled, I found that cdrecord, brasero, etc., as well as mythtv would go into unrecoverable disk wait.

After about 2 hours of playing around, it occurred to me to check for IRQ problems, and lo and behold the Linux kernel had deactivated IRQ 18, which includes the PATA controller.  I added the noirqdebug flag to grub, rebooted, and have been happy ever since.  It even solved one of the apparently unrelated, but actually closely-related, Bluetooth mouse problems I was having.  (The other, being that my MX1000 eventually disconnects and won't reconnect without manual intervention, is still there, at least as of a dist-upgrade yesterday afternoon.)

Excessively strict error checking is one of the many things that keeps Linux from being used by those with less than a software developer-level of knowledge.  What exactly are the downsides to adding noirqdebug by default, except for hardware combinations that are known *a priori* to be good?  I don't exactly have an obscure motherboard (Gigabyte GA-965P-DS3, one of the popular solid capacitor 965 boards) and most likely the issue is the IDE controller firing spurious interrupts.  Guess what?  That problem might be fixed by a BIOS upgrade, but I have zero problems if I make the kernel more permissive by adding noirqdebug, and expecting end users to upgrade their BIOS to fix a problem that has an easy workaround is yet another barrier to adoption.

From a 14-year Linux user, I beg of you: please eliminate an entire class of issues and make this the default.

Kyle

---

