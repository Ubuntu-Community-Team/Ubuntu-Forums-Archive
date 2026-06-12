---
title: "Needing a better Screen Resolution. w/ SiS graphics, drivers and xorg.conf"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by frammy7 on 2009-03-03
I'm attempting to put Ubuntu 8.10 onto a HP T5720 thin client (don't ask why, its just me being geeky). but I'm having a few problems with getting a nice screen resolution (which is a problem I seem to forever have with Linux :( and it keeps putting me off...)
I've looked up some other posts/forums about getting it to work, but I'm still stuck - so hopefully someone can help me out?!

OK. my lspci | grep VGA shows:
```
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

(which according to: [http://ubuntuforums.org/showthread.php?t=450176](http://ubuntuforums.org/showthread.php?t=450176) seems to say I have the SiS drivers installed?) and they are already ticked/installed according to Synaptic.

My xorg.conf just contains:

```
Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection
```
and thats it.

And if I go to System > Preferences > Screen Resolution I can only set it as high as 1024 x 768.

I know the graphics in the T5720 can go higher, as when it was running XP Embedded it would do 1280 x 1024 and even higher! (and I know my monitor can easily display it)..
SO... is there any way to get Ubuntu to show 1280 x 1024? Do I have the right drivers? Do I have to edit the xorg.conf file - or can I populate it automatically? As it seems to be missing a few things?! If so, where do I get the info from?
(I don't want 3D or anything fancy... just a high resolution...)

Any help would be really amazing!

---

