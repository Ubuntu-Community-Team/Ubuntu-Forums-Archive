---
title: "DynamicClocks causes hang... potential fix"
date: 2005-07-25
forum: Hardware &amp; Laptops
---

### Post by Jingo on 2005-07-25
Hello,
The graphics card of my T42 Thinkpad is an ATI Mobility Radeon 7500 (M7). Everything works fine with the open source x.org drivers, except the problems occuring after I enable the chip`s powersave function by adding the "DynamicPM" option in x.org`s config file.

After doing that the computer hangs when the boot process is over and the display gets switched to VT7, so you would normally see gdm`s login screen. The LCD turns black and I cannot switch to other VTs anymore or use the Fn combinations. The only thing left is a hardware reset and then disabling DynamicPM in recovery mode. Strangely this problem occurs only about 80% of the time, sometimes i get through to my Desktop with DynamicPM enabled.

I am using the latest ubuntu hoary, but had the same problems with warty and xfree compiled with a patch for DynamicPM(there it was still called DynamicClocks) i found somewhere on the net.

Any ideas? I would really like to use the powersaving functions.

I found a patch on [https://bugs.freedesktop.org/show_bug.cgi?id=3621](https://bugs.freedesktop.org/show_bug.cgi?id=3621) saying:
- fix dynamicclocks code.  several OUTREGs should have been OUTPLLs

Anybody tried it?

Other suggestions?

/Jingo

---

### Post by luca_linux on 2005-07-25
Try adding "DynamicClocks" instead of "DynamicPM" in X.org.
Anyway the syntax is:
```
Option "DynamicClocks" "True"
```

---

### Post by Jingo on 2005-07-25
That is not the problem. DynamicClocks and DynamicPM are aliases afaik.

It seems hardware troubles. I guess the hardware is initialised wrong.

---

