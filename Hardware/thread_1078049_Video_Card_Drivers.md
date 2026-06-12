---
title: "Video Card Drivers?"
date: 2009-02-22
forum: Hardware
---

### Post by dreamstate83 on 2009-02-22
[B][I]Hardware:
VisionTek NV996.0 Rev.D[/I][/B]

[INDENT]
I've recently installed ubuntu over a windows setup for my friend who has much less hardware then what windows requires to run. Everything is peachy except the video driver which is running on generic currently. I am convinced that the absence of this driver is why flash content slows down the system, and full screen is choppy and unplayable.

I tried using envy to install the nvidia drivers available (as that model of visiontek seems to be based on the old tnt2 if I am not mistaken) but ubuntu boots in low graphics mode until I remove the driver. I do recall an error about not having an nvidia x driver when opening the nvidia x server settings app through system > admin.

Any help is appreciated![/INDENT]

---

### Post by cariboo on 2009-02-22
The driver you need for that chipset is the nvidia-glx-71. You may want to install it manually. In a termianl type:

```
sudo apt-get install nvidia-glx-71
```

Make sure nvidia-settings gets installed also.

Jim

---

### Post by dreamstate83 on 2009-02-23
after installing the command you gave me, the only difference is that I can no longer select my widescreen monitor's native resolution. Flash is still buggy and window dragging is still choppy.

---

