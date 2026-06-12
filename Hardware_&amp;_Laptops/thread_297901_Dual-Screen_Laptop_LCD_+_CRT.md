---
title: "Dual-Screen Laptop LCD + CRT"
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by LoganK on 2006-11-11
I've installed the latest Ubuntu Edgy Eft on my Toshiba M205-S810 tablet, and it's much, much faster than Windows ever ran! (Although I am dual-booting just for compatibility). My issue is this: when I first installed Ubuntu (on the laptop connected to nothing) and when the laptop was using the first xorg.conf, I was able to get a 1400x1050 screen resolution on the built-in LCD. (I have the latest nvidia drivers installed.) I played around with my xorg.conf and got the external CRT working at 1400x1050, but with no LCD image (blank screen). I tweaked it some more and got both screens showing the same image (what I want) but at 1280x768. Obviously both are capable of displaying 1400x1050, and both can do it at the same time because that's how I've got it configured in Windows. Does anyone know how to get both the LCD and the CRT to show up at 1400x1200? I can get one or the other at 1400x1050 or both at 1280x768, but I just can't seem to make that extra step to achieve what I'd like.

All help is appreciated!

Edit: I tweaked it around some more, including specifying both of the MetaModes to be 1400x1050 (previously they were both at 1024x768), but that resulted in my CRT flickering so I manually specified a 60 Hz refresh rate (i.e., 1400x1050@60) but then my LCD displayed some crazy resolution of 1924x(other big number) which was way too big for the LCD and had the CRT display nothing - but I was able to then go to the Screen Resolution applet and see a number of different ones - I picked 1400x1050 (thankfully at 60 Hz) and clicked apply, both screens flickered but then only the CRT kept the new 1400x1050 resolution, the LCD is now blank. Am I missing something here? I'm lost...

---

