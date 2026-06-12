---
title: "Monitor displays some sort of test on wakeup"
date: 2013-08-21
forum: Hardware
---

### Post by Bubba_Jackson on 2013-08-21
Hi guys,

I'm having a problem with my Kubuntu installation. Around one or two months ago, after some package updates (probably) my computer started to display some kind of tests upon wakeup. When I leave my PC for several minutes, upon wakeup the monitor displays some kind of color tests (horizontal and vertical color bars) for a few minutes (variable duration), then it returns to normal operating mode. During this "test", it receives no input (mouse/keyboard actions do nothing). Does anyone have experience with this issue or can someone suggest a solution? I am using Kubuntu 12.04.2. I am using NVIDIA proprietary drivers.

lspci | grep VGA
```
04:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
``` 

Thanks in advance

---

### Post by VMC on 2013-08-21
Actually I disable any screen lock or wakeup. What are you waking up from - hibernate, screen saver, etc.
I have nvidia but don't install any drivers from the default install. I don't know if me trying wakeup would help you.

---

### Post by Bubba_Jackson on 2013-08-29
Turned out to be a monitor problem ;). Marking this as solved

---

