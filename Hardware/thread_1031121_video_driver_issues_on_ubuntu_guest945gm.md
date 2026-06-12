---
title: "video driver issues on ubuntu guest/945gm"
date: 2009-01-05
forum: Hardware
---

### Post by tr4shb0t on 2009-01-05
Video drivers don't seem to be working: no graphic acceleration, and can't do special visualization effects. I'm running Ubuntu as a guest with vmware.

Laptop: Dell Latitude D620
Graphics: Intel 945GM Express
vmware 6.5: vista (host), ubuntu 8.10 (guest)

I've got 'xserver-xorg-video-intel' installed, and my xorg.conf file seems strange to me, but it might be because I'm running ubuntu as a guest:

```
Section "Device"
     Identifier     "Configured Monitor"
     Options        "UseFBDev"     "true"
```

Does anyone know what the deal is?

---

### Post by igknighted on 2009-01-05
VM Guests cannot use the actual graphics chip, and therefor cannot use and 3d effects (for desktop compositing or 3d gaming).  You need to do an actual install if you want this.

---

### Post by tr4shb0t on 2009-01-05
> **igknighted said:**
> VM Guests cannot use the actual graphics chip, and therefor cannot use and 3d effects (for desktop compositing or 3d gaming).  You need to do an actual install if you want this.

Thank you. I just started using vmware and didn't realize this.

---

