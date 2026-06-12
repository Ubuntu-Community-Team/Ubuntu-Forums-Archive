---
title: "Twinview Nvidia with laptop and external VGA LCD problems"
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by peetucket on 2007-07-26
Hello,

Has anybody seen the problem with a laptop, twinview being enabled but nothing showing on the laptop panel?  I've got Feisty, the latest nvidia-glx drivers, the nvidia-setting control panel, a Toshiba Tecra M4 (with an nvidia card of course), and an external 15" flat panel.  

On it's own, the internal flat panel works great at 1400x1050.  The external LCD also works fine at 1280x1024 if I start the laptop with the flat panel plugged into the VGA port.  But if I start with the external LCD connected, my laptop panel stays black.  I've used the control panel to enable twinview and double-checked the xorg.conf.  Restarted the x-server, etc. etc.   Interestingly enough, my virtual desktop is larger in the sense that I can drag windows over to the non-functional laptop display and watch them go over on the little "virtual desktop" area on the bottom right of the screen, but of course I can't see the windows because my laptop display stays dark.

If I reverse things, boot with no external LCD connected, and then try and enable after I am booted up, I get the problem in reverse: laptop panel fine, but external LCD stays black.  

Anyone else seen this type of behavior?  Any suggestions?

Cheers!

 Peter

---

### Post by Gabmg230 on 2008-01-15
Yea, exact same problem with the tecra M5. I've looked into it quite a bit and it doesn't seem there's anything to fix that. I wonder if anyone with the tecra series has been successful at making twinview function properly.

---

