---
title: "HP dv8000 - nvidia problem"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by bharkins on 2008-01-22
On my HP dv 8000 with Nvidia GeForce Go 7600 card, I can install nvidia-glx-new (manually and with ENVY) and get Compiz to work. However, that is ONLY at resolution 1650 X 1050, which produces small fonts for normal desktop use. Reconfiguring xserver-xorg to lower resolutions, such as 1250 X 800 do not stick, and on reboot, the screen is back to the highest res. I have read many posts on HP problems and have even seen a few posters using the HP dv 8000. My question is, using the driver for 3D graphics with this hardware, is the screen supposed to be only at the high rez or have others been able to change it down? Any help appreciated.

Incidentally, on the 5 year old Dell with ATI, I can run with varying resolutions with Compiz. Go figure!

---

### Post by overdrank on 2008-01-24
> **bharkins said:**
> On my HP dv 8000 with Nvidia GeForce Go 7600 card, I can install nvidia-glx-new (manually and with ENVY) and get Compiz to work. However, that is ONLY at resolution 1650 X 1050, which produces small fonts for normal desktop use. Reconfiguring xserver-xorg to lower resolutions, such as 1250 X 800 do not stick, and on reboot, the screen is back to the highest res. I have read many posts on HP problems and have even seen a few posters using the HP dv 8000. My question is, using the driver for 3D graphics with this hardware, is the screen supposed to be only at the high rez or have others been able to change it down? Any help appreciated.

Incidentally, on the 5 year old Dell with ATI, I can run with varying resolutions with Compiz. Go figure!

HI and have you tried to adjust the resolution with nvidia-settings ```
gksudo nvidia-settings
``` this will allow you to save your settings. Good luck!

---

### Post by bharkins on 2008-01-24
> **overdrank said:**
> HI and have you tried to adjust the resolution with nvidia-settings ```
gksudo nvidia-settings
``` this will allow you to save your settings. Good luck!

That doesn't work either. Incidentally, I contacted NVIDIA tech support regarding my issue. Their (surprising) response is that NVIDIA does not support the nvidia-glx-new driver, only Ubuntu. They suggest that the correct driver is _NVIDIA-Linux-x86-169.09.pkg1.run_ . I haven't tried to install it yet but will give it a try.

Are you saying that you have a HP Pavilion 8000 w/nvidia GeForce Go 7600 running nvidia-glx-new and it does allow lower screen resolution than 1680 X 1050?

---

### Post by overdrank on 2008-01-25
> **bharkins said:**
> That doesn't work either. 
Are you saying that you have a HP Pavilion 8000 w/nvidia GeForce Go 7600 running nvidia-glx-new and it does allow lower screen resolution than 1680 X 1050?

HI and you mean it would not allow you to change the resolution? Have you checked your xorg for other resolutions? No I am not saying I have that system, I am offering help. :)

---

