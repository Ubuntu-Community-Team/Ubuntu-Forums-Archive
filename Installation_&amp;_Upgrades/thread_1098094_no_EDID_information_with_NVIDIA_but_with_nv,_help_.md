---
title: "no EDID information with NVIDIA but with nv, help extracting EDID"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by Eversmann on 2009-03-16
Hi guys!

I would like to ask you if someone knows the best way to extract the EDID information from the nv driver for use it later with nvidia propietary.

I'm running an nvidia 9500GT on a Asus P5Q with intel e7400 on a Samsung LCD 32" TV connected using the rgb cable. Installing the propietary nvidia driver (the one that comes with ubuntu, and later i've tried 180.22 and the others beta, didn't try the latest 185,xx yet) everytime i get 640x480 and the error on Xorg.0.log file about being unable to read the EDID information. 

I've searched around internet on google, on this forum, etc.. and i haven't found a clear instruction on how to get the edid file for then add it on nvidia thru xorg.conf file. 

Using the opensource nv driver the information is ok on Xorg.0.log and the correct resolution is set. on Windows is working cool too.

So, could you help me?

Thanks a lot in advance.

---

### Post by dhscaresme on 2009-10-17
Hey did you find a solution to this problem? 

My buddy is having similar problems with a samsung HDTV (LN46A630 model), however it may not be exactly the same, as I don't believe any EDID detection is happening with the "nv" driver either. Tried using compiled 185 drivers from nvidia's website, in addition to the 180 drivers from the ubuntu repos. No go on either. 

We're using a VGA cable. The machine is a Dell Inspiron 1520 with discrete Nvidia 8600 mobile chipset, running 9.04.

The nvidia-settings control panel just says that the external monitor is CRT-0, with no model number, etc. Resolution options are off, or auto.

All is good in Vista! So it's gotta be possible! 

Thanks, Jim.

---

### Post by Eversmann on 2009-10-17
I don't know how it will go with the upcoming karmic koala, but i solved it using a dvi-hdmi cable (a good one).

Everything solved.

Hope it helps.

---

