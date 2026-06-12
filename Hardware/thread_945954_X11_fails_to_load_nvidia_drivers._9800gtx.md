---
title: "X11 fails to load nvidia drivers. 9800gtx"
date: 2008-10-12
forum: Hardware
---

### Post by itsacorporatething on 2008-10-12
I have downloaded the latest nvidia drivers for the geforce 9 series, installed them, the installer automatically ran the nvidia-xconfig. 

After this I was able to use drivers fine. The nvidia logo splash screen appeared, The resolution was ok, after some editing of the xorg.conf. I was able to use fancy desktop effects like wobbly windows.

Now here is the problem. When I restarted my computer today it didn't work. X tried 3 times to load, then said that I was in basic graphics mode, using the standard "vesa" drivers. I have attempted to select the nvidia drivers from the list when you select configure, but that has similar effects.

If I use the drivers "nv" i have better results, but they obviously aren't the actual nvidia drivers. I can get the correct resolution but there isn't hardware acceleration as far as I can see.

The nvidia-xconfig tool also doesn't produce correct results either.

---

### Post by phidia on 2008-10-12
What version of ubuntu are you using, and did you upgrade to a newer kernel (do any updates)?
What you've described happens after kernel updates with manually installed nvidia drivers. But with the latest xorg.conf (hardy and intrepid) there can be problems with the nvidia driver. 

Have you tried to enable the driver from System >Admin >Hardware Drivers?

---

### Post by itsacorporatething on 2008-10-12
Ok that helps a lot. I did do the automatic updates before I shut down. It must have updated my kernel. That makes a ton of sense, because the driver modules, if I understand correctly, had to be compiled with the kernel headers. I will go through the install process again. and post here if that fixed it. Thanks Phidia!

P.S. just for the record:
1. I'm running 8.04
2. the "System>Admin>Hardware Drivers" does not list my video card, I assume because the 9800gtx is not supported by my version of Ubuntu.

---

### Post by itsacorporatething on 2008-10-12
Sucess! Ok here is a sum up:

If you are running new nvidia graphics card, chances are you will have to manually install graphics drivers.

If you manual install nvidia drivers, you must manually reinstall nvidia drivers if you update the kernel.

---

### Post by phidia on 2008-10-12
Great! you can mark this thread solved by editing the title.
Hopefully later releases of Ubuntu will support the 8 & 9 series nvidia cards.

---

