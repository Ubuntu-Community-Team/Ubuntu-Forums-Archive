---
title: "Can I install specific drivers for hardware: Xubuntu"
date: 2015-07-14
forum: Hardware
---

### Post by hashyaorite on 2015-07-14
I'm recent in the ubuntu community, xbuntu has worked out well for a college laptop I revived. This has so far been an amazing experience for me except when xubuntu took on the platform for my gaming/desktop hardware I began to encounter all this freezing as well.

Is there any possible way of installing specific drivers for certain pieces of hardware? (i.e. iCore 5 or 7, GPU or motherboard)

---

### Post by Bucky Ball on 2015-07-14
*Thread moved to **Hardware**.*

... and post moved to own thread. Please do not cross-post (hijack) on other people's threads. It's confusing and dilutes community effort, thus reducing your chances of support. By all means, keep an eye on the thread you posted on, but it is almost guaranteed the issue is not the same. The generally aren't. Too many variables, particularly hardware. 

The drivers for the hardware you mention are already present in the Ubuntu kernel, so no, you don't need to install them and no, it would be surprising if that was the cause of your issue.

---

### Post by VMC on 2015-07-14
Your freezing most likely is from your video driver. What's the output of this command:
```
lspci -vnn | grep VGA -A 12
```

---

### Post by hashyaorite on 2015-07-14
Terminal Emulator comes up with this:

lspci -vnn | grep VGA -A 12
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114 [GeForce GTX 560 Ti] [10de:1200] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ZOTAC International (MCO) Ltd. Device [19da:2227]
    Flags: bus master, fast devsel, latency 0, IRQ 60
    Memory at f8000000 (32-bit, non-prefetchable) [size=32M]
    Memory at e8000000 (64-bit, prefetchable) [size=128M]
    Memory at f0000000 (64-bit, prefetchable) [size=64M]
    I/O ports at e000 [size=128]
    Expansion ROM at fa000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau

01:00.1 Audio device [0403]: NVIDIA Corporation GF114 HDMI Audio Controller [10de:0e0c] (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. Device [19da:2227]


it appears as if my additional RAM on the graphics card is disabled

---

### Post by hashyaorite on 2015-07-14
> **VMC said:**
> Your freezing most likely is from your video driver. What's the output of this command:
```
lspci -vnn | grep VGA -A 12
```

Terminal Emulator comes up with this:

lspci -vnn | grep VGA -A 12
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114  [GeForce GTX 560 Ti] [10de:1200] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ZOTAC International (MCO) Ltd. Device [19da:2227]
    Flags: bus master, fast devsel, latency 0, IRQ 60
    Memory at f8000000 (32-bit, non-prefetchable) [size=32M]
    Memory at e8000000 (64-bit, prefetchable) [size=128M]
    Memory at f0000000 (64-bit, prefetchable) [size=64M]
    I/O ports at e000 [size=128]
    Expansion ROM at fa000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau

01:00.1 Audio device [0403]: NVIDIA Corporation GF114 HDMI Audio Controller [10de:0e0c] (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. Device [19da:2227]


it appears as if my additional RAM on the graphics card is disabled

---

### Post by hashyaorite on 2015-07-14
Excuse me

---

### Post by hashyaorite on 2015-07-15
UPDATE: I've newly moved to an edubuntu platform and so far my machine has given me no problems

---

### Post by Bucky Ball on 2015-07-15
Although resolved rather than solved, could you please mark this thread as solved as your original support question appears to have been answered. Thanks.

See the second link in my signature. 

Edubuntu's great, for the right circumstances, but not sure you need the educational packages that go with it. I could be wrong (I use the Edubuntu-artwork only myself because I like it). Good luck.

---

### Post by VMC on 2015-07-15
> **hashyaorite said:**
> 
lspci -vnn | grep VGA -A 12
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114  [GeForce GTX 560 Ti] [10de:1200] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ZOTAC International (MCO) Ltd. Device [19da:2227]
    Flags: bus master, fast devsel, latency 0, IRQ 60
    Memory at f8000000 (32-bit, non-prefetchable) [size=32M]
    Memory at e8000000 (64-bit, prefetchable) [size=128M]
    Memory at f0000000 (64-bit, prefetchable) [size=64M]
    I/O ports at e000 [size=128]
    Expansion ROM at fa000000 [disabled] [size=512K]
    Capabilities: <access denied>
    **Kernel driver in use: nouveau**
01:00.1 Audio device [0403]: NVIDIA Corporation GF114 HDMI Audio Controller [10de:0e0c] (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. Device [19da:2227]You have *nouveau* installed. You could install *nvidia* if you want to see if the freezing goes away. I can't use nouveau and have to use nvidia, else it always freezes.

---

