---
title: "AMD 7870XT Unsupported?? (Ubuntu 12.04)"
date: 2013-05-23
forum: Hardware
---

### Post by w0ss4g3 on 2013-05-23
I cannot get this card to work properly! Ideally I want to use either Cat 13.1 or 13.4, but whichever I install (via this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx) or using the manual way) I always get the unsupported hardware watermark and when I use amdconfig (e.g. I'd like to run amdconfig --initial) I get:

amdconfig: No supported adapters detected

I'm pretty confused as I've had an AMD card on this system before and it worked fine. The card works fine under windows, so I don't think that it's to blame. The card seems to be detected in the AMD CCC as it lists "AMD 7800 series". Also I can see the card with:

lspci | grep AMD
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 679e
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Tahiti XT HDMI Audio [Radeon HD 7970 Series]

Despite all this, I've been able to set up my dual monitors with Xinerama although there is notice lag/tearing when I move a window about for example.. so I'm quite sure something is wrong.

Can anyone offer any help?

Thanks in advance.

---

### Post by w0ss4g3 on 2013-05-24
Still failed to fix this.. bump :/

---

### Post by jacksaff on 2013-05-24
Have you tried to install drivers using the "Additional Drivers" app?
It's in the system menu on kubuntu, not sure where to find it on unity.
This is the supported method for getting proprietary video drivers going.
If the driver you have works, the 'unsupported' watermark can be removed - you will have to google for how.

---

