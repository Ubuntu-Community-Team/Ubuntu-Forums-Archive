---
title: "Random freeze and system instabilty using Kernel 5.19.0.32-generic on 22.04 LTS"
date: 2023-02-26
forum: Hardware
---

### Post by arshakjafar on 2023-02-26
Hi,


A few days ago, my laptop (ASUS TUF A15 with Ryzen 7 5800H + RTX 3060) froze suddenly but the audio kept playing. Over the next few days, this became more frequent along with random artifacts on the screen. 
Some of these were icon descriptions saying on the screen (like an LED Burn in) for quite sometime long after the pointer has been moved, windows having weird behaviors while opening and dragging around. 


The error log highlighted one message in particular. ```
nvrm cpuidinfoamd unrecognized amd processor in cpuidinfoamd
```


I uninstalled all the GPU and AMD drivers to the point ubuntu booted straight to CLI. I then reinstalled ```
ubuntu-desktop
``` but the problem didnt go away. I switched between different proprietary nvidia-drivers and open source. The problem still persists.
That is when I decided to switch kernal in the ubuntu boot menu, and it helped. Switching Kernel to 5.15.0.60 generic from 5.19.0.32-generic seems to have fixed the issue.


Anyone knows what is the cause for the issue on 5.19.0.32-generic ? and will the issue persist in the versions that comes after 5.19.0.32-generic ?


TIA

---

### Post by mIk3_08 on 2023-02-26
> **arshakjafar said:**
> That is when I decided to switch kernal in  the ubuntu boot menu, and it helped. Switching Kernel to 5.15.0.60  generic from 5.19.0.32-generic seems to have fixed the issue.

I don't have any idea on this. But thanks a lot for sharing  the process of fixing the issue. This will help to others who will  encounter same issue like this. Regards and cheers.

---

