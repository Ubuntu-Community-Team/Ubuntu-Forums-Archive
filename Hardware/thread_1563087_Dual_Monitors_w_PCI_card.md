---
title: "Dual Monitors w/ PCI card"
date: 2010-08-28
forum: Hardware
---

### Post by flyingboy on 2010-08-28
Hey,
Is it possible to enable my onboard graphics in addition to my PCI card? My card makes it so the only ports outputting info are DVI, S-Video, and HDMI, but the onboard has a VGA output. My current and main monitor uses either DVI or VGA (weird that it doesn't have HDMI considering its relatively new) and the secondary monitor only takes VGA. 

Thanks!

---

### Post by Fafler on 2010-08-28
It should be possible. First do a

lspci | grep VGA 

to identify your cards. Another solution would be using a HDMI - DVI adapter to use your primary monitor on the HDMI port and a DVI - VGA adapter to use your secondary monitor on the DVI port.

---

### Post by flyingboy on 2010-08-28
"02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)" is the response

---

### Post by cascade9 on 2010-08-29
Might be possible, but quite a few onboard video chips will disable themselves if there is a video card in the computer. Then there would be all the sodding around to get the thing going, if it does work....

Might be easier to use a DVI-> VGA adapter for the 'old' monitor, then a HDMI-> DVI for the 'new'. 

BTW, not all new monitors have a HDMI. I've just grabbed a new LED LCD monitor, and it has no HDMI.

---

### Post by flyingboy on 2010-08-30
In the end, I simply bought the adapters from newegg. Spent twelve bucks; if i got it from bestbuy it would've been fifty.

Thanks for all the help!

---

