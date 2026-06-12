---
title: "lm-sensors and hddtemp"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by Matakoo on 2007-06-19
Hi,

I'm not sure if this is something I should be concerned about, since I'm not sure what normal values should be.

lm-senors and hddtemp are correctly installed and configured, and I do get some values out of temperature/sensor aware programs (such as Kima). 

The CPU temperature fluctuates between around 26 - 35 C (Intel Celeron D@3.5 Ghz)
Both harddrives report temperature of 41-43 C (plus/minus a degree or two)
The GPU usually is around 63 C (Nvidia GeForce 7300 GS).

This system is in a BigTower case so there should be enough airflow with all the fans in there. Although the sensors command scream ALARM at Sys Temp (43 degrees, and apparently sensors thinks its hysterical as soon as its above zero degrees).

The sensors program also ALARMS me in regards to the voltage sensors.

Is this something I should be concerned about?

---

### Post by tgalati4 on 2007-06-19
There is an lm-sensors configuration file that you can edit to set your alarms to whatever you want them to be.  The default settings are usually wrong, so it's not something to worry about.  

Your graphics card is a little toasty.

---

### Post by Matakoo on 2007-06-20
> **tgalati4 said:**
> There is an lm-sensors configuration file that you can edit to set your alarms to whatever you want them to be.  The default settings are usually wrong, so it's not something to worry about.  

That's what I thought. But better safe than sorry. Besides, I'm mostly interested in keeping an eye on the temperatures and the fans so if the other values are out-of-whack is no big deal.

> **tgalati4 said:**
>  Your graphics card is a little toasty.

Actually, it seems like it's not. I thought it was, despite what the nvidia-settings program tells me. According to that program,  I'm nowhere near  being  close to having a too hot GPU.  Anyway, I managed to find  some info on a Nvidia forum and it seems like temperatures between 65 - 75 degrees C are normal when utilizing the 3D-functions of modern cards (as in: using Vista or Beryl/Compiz...).

---

