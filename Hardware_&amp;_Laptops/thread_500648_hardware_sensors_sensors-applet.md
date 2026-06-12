---
title: "hardware sensors sensors-applet"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by fakie_flip on 2007-07-14
I am having problems with sensors-applet. It is
 not displaying my core cpu temps, but the sensors
 command shows that they temperatures are being
 read by lm-sensors. iI am unable to get
 sensors-applet to display my video card temperature, but my
 video card temperature is being read by the
 nvidia driver. All of this is shown in the picture.

[http://img209.imageshack.us/img209/2084/sensorsappletvi5.png](http://img209.imageshack.us/img209/2084/sensorsappletvi5.png)

---

### Post by fakie_flip on 2007-07-18
bump!!!!!!!!!!!

---

### Post by dabl on 2007-07-18
I like "xsensors" for sensor output display in Ubuntu.  It's a package that you can select with Synaptic. It installs in "Applications>System Tools"  :)

---

### Post by rfurman24 on 2007-09-10
I have the same issue. I can not find an answer that is amd specific and do not know if the intel answers will work. The "sensors" command shows core temps but lm sensors will not in the the sensors applet. It just says chip not found.

---

### Post by fakie_flip on 2007-09-15
bump!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Chip not found <-- still says this

I upgraded to version 1.8.1-1 by compiling it, and I still have the bug. Also, I did not use the Envy junk or nvidia-glx packages to install the nvidia driver. I downloaded the driver from nvidia.com. Now because of that, I can't read my temperature from the sensors-applet for my video card however the temperature shows when I run nvidia-settings.

---

### Post by IanW on 2007-10-15
From what I've read elsewhere, the Gnome sensors-applet needs to be re-compiled to read the nvidia temps.

---

### Post by Perkins on 2007-11-10
Correct.  sensors-applet must be compiled with the nvidia support turned on.

Unfortunately, this requires the nvidia libraries.  They were supposed to be in the nvidia-control package, but they're not.  Anybody know where to actually find NVctrl.h?

---

