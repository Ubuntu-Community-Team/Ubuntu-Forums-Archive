---
title: "ububntu 10.04 - problems with nvidiga g105m"
date: 2010-05-02
forum: Hardware
---

### Post by Raido on 2010-05-02
I'm using asus ux50v with nvidia g105m and the problem is that after installation of the driver and reboot, screen just turns black and don't turns on even in recovery mod.
The only thing I could do was reinstalling the system, still it's rather sad to live without hardware acceleration.
I guess there's something to be done with xorg.conf, but I'm pretty new to all this.
Extremely thankful in advance for your advice))

---

### Post by marinerk09 on 2010-06-30
AHH finally someone else with the same problem!  I'm a total n00b but I'm in love with Linux and it's working FLAWLESSLY except for this problem! its driving me nuts!

---

### Post by psygen on 2010-07-31
I also have the same problem. My laptop is an HP DM3T with adapter nVidia G105M. Even removing the nouveau and installing the latest version of driver nvidia, when I run nvidia-detector not appears that there is an adapter nvidia on my system.

---

### Post by marinerk09 on 2010-12-20
i take it no one has found a solution for this yet:confused:

---

### Post by psygen on 2010-12-21
I upgrade for 10.10, but this problem persist. This problem is related to hybrid cards (nvidia+intel), where the support in Ubuntu / Linux is still crawling. The vgaswitcheroo even works (after exhaustive settings), but still not good.

---

### Post by joshuac2651 on 2010-12-21
I'm having the same problem
I have a lenovo y560 
Ati Radeon HD 5730

after installing the graphics drivers and restarting ubuntu begins to boot up then the screen goes black.

Any solutions

---

### Post by Jan051 on 2010-12-30
Same problem here, Ubuntu 10.04.1 64 bit on an HP DM3 with the nvidia g105m graphics card. 
I can not set the screen brightness either, so battery life short. Sucks, now I am forced to use windows on this machine :(
Does anyone know whether this problem is also present in the 32 bit version?

---

### Post by psygen on 2011-01-03
I gave up the NVidia driver. I'm using the Nouveau driver and works without problems, even with Compiz. Now the question to switch between Intel and Nvidia to save energy, it does not work. The screen resolution of 1024x768 mode is not stretch.

Ubuntu 10.10 64-bit

```

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
01:00.0 VGA compatible controller: nVidia Corporation G98M [GeForce G105M] (rev a2)

```

```

lsmod | grep nouveau
nouveau               569200  0 
ttm                    68212  1 nouveau
drm_kms_helper         32836  2 nouveau,i915
drm                   206230  7 nouveau,i915,ttm,drm_kms_helper
i2c_algo_bit            6208  2 nouveau,i915

```

---

