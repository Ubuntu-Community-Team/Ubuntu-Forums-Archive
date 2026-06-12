---
title: "PCIe TV tuner card conflicting with FGLRX"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by devguy on 2009-09-05
Hey guys.  I got an interesting problem.  I'm currently running a Phenom II x4 system on an ASUS 790FX board with an XFX Radeon HD 4870 1GB using ATIs FGLRX (Cat 9.8 ) with Ubuntu Jaunty x64.

I just purchased a "new" tv tuner card, the ASUS/Gateway combo-210e PCIe card.  Now I know that Linux has poor support for all PCIe tuner cards, but this is a little troubling.  My issue is that having the tuner card in my pc when booting, I get an FGLRX conflict.  It is as if FGLRX is trying to apply the driver to the tv tuner card.

My 4870 is running on 05:00.0 and I'm getting an error on boot about device 06:00.0 not being found by FGLRX.  I chose the edit configuration option on the safe mode VGA driver boot, and found a reference to the 06:00.0 as an FGLRX device, and I removed that (obviously leaving the device at 05:00.0 alone).  However, the problem still persists.

My Ubuntu machine works perfectly fine without the card installed.  Any ideas?

---

### Post by devguy on 2009-09-10
Well, the problem was the FGLRX driver didn't like the pcie slot I put the card in.  Apparently, it was trying to crossfire my 4870 with the tv tuner and that was giving it problems.  

Putting it into a different PCIe slot fixed the problem.  However, still no TV tuner support out of the box for this card with VLC or MythTV...

---

