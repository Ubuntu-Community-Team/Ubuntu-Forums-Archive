---
title: "Thinkpad W540 palmrest overheat issue"
date: 2020-05-20
forum: Hardware
---

### Post by mceoletta on 2020-05-20
Good day, this is my first post here so please tell me if i'm in the wrong section.
I have a thinkpad W540 with a discrete GPU (Nvidia quadro k1100m) and the thing runs really hot under Ubuntu while it should not.

The gpu chip is under the left palmrest of the machine, and when the gpu is heavily utilized a heating of the area is to be expected (this happens on Windows), if the gpu is disabled via Nvidia driver or is not used the palmrest is stone cold.
If I run Ubuntu on the machine (I tried 18.04 LTS and 20.04 LTS, identical outcome) the palmrest is really hot some minutes after boot (even if the PC is idling on desktop). I'm sure this is not an hardware problem because under Windows is perfectly fine. To further confirm this I tried the same on an identical W540 with the same result.

I tried installing different drivers (nouveau and proprietary Nvidia 390, both on 20.04 and 18.04) and sadly it makes no difference at all. From Nvidia control panel (with Nvidia driver installed) I saw that the gpu clock is always at 705MHz. This might explain the heating: the gpu is in a high power state doing nothing ](*,). 
Do you guys know a way to prevent this? I don't care about the discrete gpu at all (might as well disable it permanently) but I do care about my wrist health and this thing is driving me crazy. 
Sadly this device does not allow to disable the discrete gpu in bios so the only way out is either to fix the driver issue or change my laptop.

If you have any suggestion on what to do this is greatly appreciated.
Thanks in advance and if you need further information I can provide them
Marco

---

### Post by mceoletta on 2020-05-22
bump, I add the output of dmesg
[https://paste.ubuntu.com/p/YMskXfQZsT/](https://paste.ubuntu.com/p/YMskXfQZsT/)

---

