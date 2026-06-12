---
title: "Ubuntu 6.06 on Mac Mini Core Duo"
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by AllBuntu on 2006-07-04
Hi,

I have this Mac Mini draggin its feet in Mac OS X. Wanting to turn it into an Ubuntu redundant server, I installed Boot Camp but got trouble installing Ubuntu after that using two of the the 6.06 CDs. I wasted some time on the following attempts:
a) LiveCD install from GNOME (crashes at end of copying session, black screen, two white squares)
b) Alternate CD, text-mode install (crashes at end of copying session, black screen, two white squares)
c) Alternate CD, text-mode server install (hangs at installing elilo with install screen at 50%)

It suddenly struck me I don't need boot camp to do this... ...had enough of Windows anyway!

So how about a few pointers from the community: what is the best way?
1. Should I install Ubuntu 6.06 on the Mac Mini Code Duo with or without Apple's boot camp?
2. Should I start from the Desktop CD, the Server Install CD, or the Alternate CD?
3. Is there a how-to out there for this already (have not found one, they are all Debian or legacy Mac)?

I would be happy to boot into mac OS X once every christmas as a present. Once Ubuntu is running, this mac will second all my server tasks (Wiki, database, Web services) plus running a redundant Windows server using VMware. Hey, that's 20 dBA at the operator position!

Grateful for any help and advice out there...

-H

Actually, here are som survival tricks for non mac users:
Four seconds pressing the power button turns off a hosed mac
pressing the C key during boot starts from the CD
pressing F12 for two seconds (on a pc keyboard) ejects the CD during boot (hey, there's no eject button)
If the mac system is not booting, start using the mac install disk 1. It can do a full install, repair partitions using the disk utility, and has a password reset utility for that situation.
Good tricks on the way to Ubuntu land!

---

### Post by AllBuntu on 2006-07-05
Ok it's been four hours:

I suspect the BootCamp stuff should be used.
The Desktop CD works if you use the Safe Graphics choice at the bootup menu. Howver, installer runs until grub, then it crashes (Mac uses the new GPT partitioning system and has EFI instead of BIOS, that's why.)

[this]("http://www.fi.ameslab.gov/Projects/mini-xen/index.html") Xen guy  recommends to download [grub_0.97-1ubuntu9_i386.deb]("http://www.fi.ameslab.gov/Projects/mini-xen/grub_0.97-1ubuntu9_i386.deb") that might enable install to finish.

...and then over [here]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp#Booting_your_mac_via_rEFIt") Booting your mac via rEFIt is described (some EFI compatible boot menu understanding Linux.)

Maybe that works if there are no other suggestions?

---

