---
title: "laptop won't boot when power unplugged after kernel update"
date: 2009-01-29
forum: Hardware
---

### Post by pjizz on 2009-01-29
Hi all,

I've been having a problem for a while now and haven't come across or devised a solution.  Basically, when I don't have the power plugged in on my lappy, Ubuntu won't boot up with the two newest releases of the kernel.  I have to hit escape and go to the GRUB menu and select an older kernel for it to work.  2.6.27-9-generic doesn't work, only 2.6.27-7-generic works.  However, this isn't a problem when the power is plugged in.  I thought it might be fixed with the new kernel release 2.6.27-11-generic but the problem is still there.  Any thoughts/suggestions?  I know I'm not the only one with this problem.

relevant data: dell latitude d600, ubuntu 8.10,

---

### Post by pjizz on 2009-01-30
in a shameless attempt to bump....

I did forget to mention that a simple fix (not a solution) for anyone running into a similar problem is to simply edit the GrUB configuration file in /boot/grub/menu.lst and set the working kernel to default

i still would like a fix though...what good is a new kernel if you can't boot it up, and what good is a laptop if you have to always carry around a clunky power adapter

---

