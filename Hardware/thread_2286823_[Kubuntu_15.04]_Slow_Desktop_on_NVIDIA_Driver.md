---
title: "[Kubuntu 15.04] Slow Desktop on NVIDIA Driver"
date: 2015-07-14
forum: Hardware
---

### Post by Hamish_Claxton on 2015-07-14
Hey Guys,

Having another issue on my laptop. After doing some testing I noticed that when running on the NVIDIA Driver the desktop slows down quite a lot. Even tasks such as copying data have a severe impact on performance.
I've done some of my own research to find a fix but so far none of the available fixes have resolved my issue. I've also started coming across a major issue when changing the resolution. Whenever I do so, it causes major 
graphical corruption and requires a forced reboot. See below screenshot. I've also tried multiple NVIDIA Drivers - 346.59, 346.82, 352.21.
[ATTACH=CONFIG]263204[/ATTACH]

I'm currently running a Dell Precision M4800:
```

Intel i7-4800MQ
NVIDIA Quadro K1100M
16GB of RAM

```

Here's a Hardinfo Report for those who are curious:
[https://mega.nz/#!RZRRFSRI!jgwFQRTLugJQsx6J4jHciwviSK6BlVME1UcDgRbOHu0](https://mega.nz/#!RZRRFSRI!jgwFQRTLugJQsx6J4jHciwviSK6BlVME1UcDgRbOHu0)

Thanks,
Hamish

---

### Post by Hamish_Claxton on 2015-07-16
Issue fixed by downgrading to Kubuntu 14.04 and using KDE 4. Looks like KDE 5 has major graphical performance issues on NVIDIA. At least for the Quadro K1100M anyway.

---

