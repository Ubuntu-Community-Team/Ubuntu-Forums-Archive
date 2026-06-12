---
title: "ntpd starting and stopping after upgrade"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by jordon on 2009-11-01
I upgraded from 9.04 to 9.10 by downloading the alternate CD and mounting its ISO image. That seemed to go fine, but while restarting, ntpd starts and stops continuously as if in an infinite loop. I can't Ctrl-C out of it, so I'm stuck having to power down.

When I boot into recovery mode, I can get to a root terminal with networking, no problem. I can also select dpkg, which tells me I still have a bunch of packages that need to be upgraded (the same ones as before? I'm not sure). I started downloading those but it kept prompting me to insert the CD, which I didn't physically have, so I canceled that.

If I try to continue the regular boot process after being in recovery mode, Ubuntu starts going through the usual steps, but after checking the battery status (I'm on a laptop), it stops, and I'm again stuck having to power down.

I can select the previous kernel from the GRUB menu, but Ubuntu gets confused about which splash screen to display during the boot, and at the GDM login window my mouse doesn't work, so I decided not to continue with that.

Can anyone help? I'd at least like to know how to stop ntpd from starting automatically if I have a root terminal, but if someone knows a better way to fix the problem, I'd be very grateful. I don't want to have to do a clean reinstall.

(Edit: I've just gone ahead and reinstalled.)

---

