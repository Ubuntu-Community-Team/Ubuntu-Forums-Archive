---
title: "Problems with VIA K8M800 graphics chipset"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by Jguy101 on 2007-06-02
My PC running Feisty 32-bit has a VIA Technologies K8M800 graphics chipset, and I have the proper drivers installed. I'm having some problems, though.

The first is that I can't set my resolution beyond 1024x768, even after editing /etc/X11/xorg.conf so I can use 1280x1024 (in fact, even after eliminate 640x480 as an option, it still shows up in the list when I open the Screen Resolution prefs). Whenever I try to run a game called Battlestar Galactica: Beyond the Red Line, it won't run, because it claims my resolution is too low (it thinks I'm at 512x512, while I'm obviously not).

I've encountered another problem while running the game [YSFlight](http://www.ysflight.com). Within the first ten seconds of simulation, my system will freeze.

Any ideas on how to fix these problems?

---

### Post by coffeecat on 2007-06-02
I was able to get 1680x1050 resolution on a machine with the same VIA chipset, so you should be able to get 1280x1024. Have a look in the Driver line of Section "Device" of xorg.conf. If that's showing as "vesa", change it to "via".

I've seen a few posts around where vesa has been set up in xorg.conf for some reason instead of the chip-specific driver. The vesa driver is very limited.

Also, the highest resolution needs to be specified first in the 'Modes' lines of the Screens section, so removing 640x480 wouldn't have the effect you want.

---

### Post by Jguy101 on 2007-06-02
I already have the driver specified as "via", and I did add 1280x1024 after removing 640x480.

---

### Post by coffeecat on 2007-06-03
> **Jguy101 said:**
> I already have the driver specified as "via", and I did add 1280x1024 after removing 640x480.

That's strange.

This sounds like a silly question, but it must be asked. Are you sure that your monitor can support 1280x1024 resolution? What type is it? What size? Does the handbook give a list of supported resolutions?

---

### Post by Jguy101 on 2007-06-04
Yes, I'm absolutely positive - that's what it was running at when I ran Windows. It's a 17" Proview flat CRT.

---

