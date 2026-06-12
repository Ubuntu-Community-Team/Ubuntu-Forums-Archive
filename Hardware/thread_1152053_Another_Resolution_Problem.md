---
title: "Another Resolution Problem"
date: 2009-05-07
forum: Hardware
---

### Post by tydfil on 2009-05-07
Running Jaunty.  Have Nvidia 180.51 driver.  Have used the nvidia settings in terminal to change resolution to 1680x1050 (native for my monitor), but reverts to 1024x768 when I reboot.  

Interestingly the login screen appears to be at the correct resolution and the resolution drops as the desktop loads. Using Auto in the settings sets the screen at the right resolution, but only for that session.  I have aquired and used the EDID but that does not work.  

I have the same isseu on dvi and analogue.

:(

---

### Post by overdrank on 2009-05-07
Hi and if you are using the nvidia-settings to adjust your resolution ```
gksu nvidia-settings
``` have you save it to your x-configuration in the nvidia-settings also?

---

### Post by tydfil on 2009-05-07
Thanks for the quick reply overdrank. Yes I have saved the settings. I have attached a copy of xorg.conf if it helps.

---

### Post by tydfil on 2009-05-08
An update on this problem.  Can anyone sugest a solution to this problem given this enrty in the xorg log:

CVT (DFP-0)'s EDID does not contain a maximum image size;
(WW) NVIDIA(0):     cannot compute DPI from CVT (DFP-0)'s EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default

---

