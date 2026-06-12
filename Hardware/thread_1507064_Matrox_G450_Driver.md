---
title: "Matrox G450 Driver"
date: 2010-06-11
forum: Hardware
---

### Post by Amadameus on 2010-06-11
Okay, so after doing plenty of research and trying several fixes on my own, I've had no luck - so I'm turning to the good people on UForums for help.

I've finally got my friend convinced to try Ubuntu, so I set him up with a 9.10 disc I had and am currently trying to configure his box.

He has two monitors.
Ubuntu does not detect either monitor, no matter the hardware configuration.
It mirrors the signal, however we're trying to set up dual monitor display.

lspci returned this result as the only VGA entry:
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 82)

Naturally, I went and grabbed Matrox's G400/G450 drivers from [their website](http://www.matrox.com/graphics/en/).
Installed, still no response from the rig.

There is no xorg.conf file
System > Preferences > Display shows that there is "Unknown" monitors, so the box appears to be spitting out VGA information blind.

...has anyone else had this issue, or could they direct me to a solution? My best Google-fu has failed to find one.

---

