---
title: "NVidia Fan Problems"
date: 2013-09-20
forum: Hardware
---

### Post by vkyo on 2013-09-20
Hi all,

I'm running a PC with Ubuntu 13.04 and an NVidia Quadro FX 5800 Graphics card. My problem is that upon startup, my fan always runs at 100%, and I need to run nvidia-settings to adjust the fan speed. Is there any way to set the fan speed to, say, 70% automatically at startup?

Thanks :)

---

### Post by Yellow Pasque on 2013-09-21
See if these commands do it:
```
nvidia-settings -a [gpu:0]/GPUFanControlState=1
nvidia-settings -a [fan:0]/GPUCurrentFanSpeed=70
```

If that works, then you just need to find a way to do it at startup.

---

