---
title: "3D driver won't load in 9.04"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by MyInstallationNeedsHelp on 2009-04-24
In 8.04, I had working 3D.  In 9.04, I do not.  I have a GeForce2 Pro card.  That appears to require the nvidia-glx-71 binary Xorg driver.  I installed that with synaptic, but the driver doesn't load.  My X.org file only contains:

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

So it doesn't look like the driver is really getting installed properly or loading.  How can I get it properly installed, loaded, and configured?

Thanks!

---

