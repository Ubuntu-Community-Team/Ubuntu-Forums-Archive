---
title: "ATI Catalyst 11.2 segmentation fault maverick"
date: 2011-03-22
forum: Hardware
---

### Post by s4ms3milia on 2011-03-22
Hey,

i just upgraded from what I think must have been a 10.x driver and after a fresh install this happens:

```
$ fglrxinfo
Segmentation fault
$ fgl_glxgears
Using GLX_SGIX_pbuffer
Segmentation fault
```

I followed [this]("http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Updated_Open_Source_Driver_PPA.27s") guide step by step.

Anybody having similar issues and maybe solved them? 

Best regards!

---

### Post by mwacky on 2011-04-15
I get the exact same message what is your hardware?

Mine is ATI Radeon Xpress 200M.

According to the guide:
"The ATI Radeon 9500-9800, Xpress200-1250, 690G, 740G, X300-X2500 (including Mobility RadeonHD 2300, since it is really a DirectX 9 part). See the complete list here. If your card is on that list, you are limited to open-source drivers on Ubuntu Lucid/10.04 (and later). If you really need the proprietary Catalyst/fglrx driver, you will have to use an older Linux distribution, such as Debian Lenny/5.0.x or Ubuntu Hardy/8.04.x. "

So it sounds as if I am limited to the open source driver.  I believe this is true because with older versions of Ubuntu the proprietary drivers used to handle it easily.  I'm guessing if the manufacturer dropped support it made it harder that to work.

---

