---
title: "nvidia sound card is not working"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by asprakash on 2007-09-28
I installed Ubuntu gutsy in my acer laptop.
my laptop configuration is,
dual-core AMD Athlon 64 X2
Nvidia Geforce go 7000
nVidia high definition audio codec (when i check with lspci)
Nvidia nforce
I installed the drivers from nvidia portal. My network card and video card is working fine. But my sound card is not working. When i checked with windows xp all the hardwares are working fine. 
In windows, the sound card is working fine with Realtek driver. I tried with  Realtek also. But no use in Linux. I tried with other distros like, FC6, Open suse and Debian. None of distros supports this sound card. Help me solve this problem.
Getting bored without sound in my Lapy..:(

---

### Post by ddrichardson on 2007-09-28
If it's the nVidia Realtek HDA (Rev 2) card then I'm afraid the balls with ALSA on this one. The driver doesn't work - the card will appear to work but will not actually make any sound. I've been wrestling with this driver for nearly a year now and I just cannot get the required information on its implementation despite several people on these forums helping provide pinout diagrams and datasheets.

The problem seems to lie in the integrated modem chipset rather than the card itself which usually requires a little tweaking in alsabase to configure.

If you have followed the intel-hda howto on the wiki and have had no joy then this is probably the same place that I'm in now.

I purchased a £15 set of USB laptop speakers so now have sound on that machine, but to be honest only use it for compiling now because it annoys me so much.

---

