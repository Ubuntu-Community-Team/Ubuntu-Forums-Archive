---
title: "Touchscreen with dead zone"
date: 2017-10-07
forum: Hardware
---

### Post by kaz-kanso on 2017-10-07
I have come across a strange issue in that part of the touch screen on the laptop I am using appears to be dead, which initially I assumed was a hardware issue. However, after further investigation I dont believe this is the case.

The dead zone only became noticeable in the last coupe days. It is a rectangle that spans from approx 70% to 85% of the horizontal, and from the top to almost the bottom of the screen. I have diagnosed this by using the following command to view the raw data being returned from the touch screen:

```
hexdump -C /dev/usb/hiddev0
```

When touching the affected parts of the screen, no data is produced, and when touching other parts I see the data streaming. However, when booting to a live version of Ubuntu 17.04 (with the same kernel as the installed OS: 4.10.0-19) the whole touch screen works as expected (and verified using the above command to see the raw data). Also, from within Windows the touch screen works as expected too.

Is there any way to debug this further? I suspect that reinstalling the OS will fix the issue, but I was hoping to understand why it is happening.

---

