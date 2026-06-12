---
title: "Automatic reboot after suspend to disk due to USB"
date: 2008-08-11
forum: Hardware
---

### Post by jvitense on 2008-08-11
Hi there!

I have a problem with suspend to disk on my laptop. When I choose to suspend to disk, the laptop doesn't stay switched off after suspending, but reboots after some seconds, restoring the system to the point when I clicked on suspend to disk. I realized that my usb mouse stays powered on all the time during this power down - power up cycle. When I remove the mouse before clicking on suspend to disk, everything works fine.
I read something about soft halt (S5), that wouldn't power down the laptop completely in some cases. As for me, I would like to have my laptop power down completely after a suspend to disk, and I don't want it to reboot on its own. Any ideas what I could do? Thanks a lot!
I'm running Ubuntu 8.04 with kernel 2.6.24-20-generic on a HP Compaq 6720s laptop.
   Jan

---

### Post by jvitense on 2008-08-20
Hi there!

I found a workaround that fixed the problem:

Edit /usr/lib/pm-utils/functions and replace "platform" with "shutdown".

Source:
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/226069]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/226069")

Greetings,
   Jan

---

### Post by esplinter on 2008-10-16
this worked partially for me. Now my laptop suspends ok but just after suspend it reboots ....

---

