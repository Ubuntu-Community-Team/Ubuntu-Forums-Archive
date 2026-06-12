---
title: "Can't enable compiz effects on an Intel card"
date: 2009-12-04
forum: Hardware
---

### Post by turinturambar on 2009-12-04
I just installed Ubuntu Karmic on my mother's Dell Dimension 2400.  From the Appearance window, I can't enable desktop effects.  This is my graphics output of lspci:

00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

After doing some googling I am still not much wiser, I have a tar.gz package from Intel that might provide a driver and I will try that next.  Apparently my card is blacklisted(?). Another website suggested running

SKIP_CHECKS=yes compiz-manager

to bypass the compiz blacklist.  After running the screen froze, showing only the desktop image, no gnome panels.  After eight hours, I restarted, but I still cannot enable effects.

Any advice?

Thanks

---

