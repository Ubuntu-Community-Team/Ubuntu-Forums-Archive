---
title: "Incorrect Graphics Driver on Toshiba c855d"
date: 2020-07-15
forum: Hardware
---

### Post by jackpc32 on 2020-07-15
I've been struggling to get proper display drivers for my laptop. It is running 32 bit Ubuntu 16.04 LTS. It currently identifies it as some sort of amd palm. Ubuntu automatically did this. I have dpkged every file I can get from amd. I dont feel like a laptop from 2009 should struggle with 144p youtube.

---

### Post by Yellow Pasque on 2020-07-15
The proper driver is built into the kernel.  Proprietary AMD drivers are not an option for a GPU this old, even on Ubuntu 16.04.

> I have dpkged every file I can get from amd.
That was.... not a good idea. There is no telling what state your system is in now. What does glxinfo or glxinfo -B tell you?
```
glxinfo -B
```

> I dont feel like a laptop from 2009 should struggle with 144p youtube
The year does not tell the whole story. From looking at the specs of various c855d models, it looks they used low-speed "ultra mobile" APU's to begin with (great for battery life, not so much for performance). Also, video decode acceleration in web browsers on Linux has been non-existent until recently. If the system struggles with video playback in a browser, the GPU/driver has little to do with it, because the "heavy lifting" is being done on the CPU.

I'm wondering if it is possible for you to try a LiveUSB of 20.04 and see how that performs?

---

