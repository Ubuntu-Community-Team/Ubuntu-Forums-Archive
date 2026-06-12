---
title: "help with intel 945 xorg.conf"
date: 2008-11-10
forum: Hardware
---

### Post by newb2008 on 2008-11-10
Hi,

I was wondering if anyone could tell me what my xorg.conf should look like for a Toshiba Satellite A135-S4527 with an Intel GMA 945 graphics card (i.e. what should the inputs be for the graphics card?). 

I'm not convinced Ubuntu is using the card. It was suggested here [http://www.geocities.com/sikofitt/](http://www.geocities.com/sikofitt/) that I use the i810 driver but I can't seem to alter the xorg.conf file to do that. Currently it says this: 

Section "Device"
   Identifier "Configured Video Device"
   Option     "UseFBDev"               "true"
End Section

Any suggestions? Thanks in advance.

---

