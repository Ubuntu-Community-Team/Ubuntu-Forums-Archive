---
title: "Kernel update breaks xserver and sound"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by philstovell on 2008-12-16
This morning Ubuntu upgraded itself to 8.04.2. This included a kernel update, to 2.6.24-23. This broke the x-server, it would only start in low-resolution mode. I have a nvidia GeForce 8400 GS, which was unrecognized, there was nothing in the hardware drivers application. Sound also didn't work. I reconfigured the xserver from a recovery session, and got back to the correct resolution (1440x900), but without the nvidia drivers. Still no sound. I rebooted to the previous kernel and everything is back as it should be.

It looks like kernel 2.6.24-23 breaks nvidia and sound.

---

### Post by juanoleso on 2008-12-17
had same problem but with older hardware:
```
 nVidia Corporation NV36 [GeForce FX 5700LE]
```
I guess I'll try and go back to the old kernel.  I DL'd the Nvidia drivers from the site to get my video drivers working, but the sound drivers are missing:
```
nVidia Corporation nForce2 AC97 Audio Controler
```

---

### Post by elektrolott on 2008-12-17
I have a Thinkpad T61 (with intel graphics) and after the upgrade I have no sound and no wireless.

My workaround so far is to select an older kernel in the GRUB menu at boot time.

---

### Post by philstovell on 2008-12-17
I reloaded update manager later in the day and got 8 updates. This cured the problem. I suspect having proposed updates selected is the culprit, which I've removed (and backports).

---

