---
title: "How to Get Ubuntu to Recognize a Standard Monitor"
date: 2011-04-25
forum: Hardware
---

### Post by feed5000 on 2011-04-25
I have a lab of 24 computers with Ubuntu 10.10. They all have the same 17" Acer monitor. For some reason, 4 of them are "unknown" in System > Preferences > Monitors.

The other 20 monitors are all listed as "Acer Technologies 17"", and I can change the Resolution, Refresh rate, and Rotation.

But the settings of the "unknown" 4 are unchangeable. The resolution is stuck at 1280x1024, the refresh stuck at 0 Hz, and the rotation stuck at Normal.

Anybody know how I can get my other four systems to recognise the Acer monitor? Thanks!

---

### Post by feed5000 on 2011-04-25
Some information on one of the computers that fails to recognise the Acer monitor.

```
icrs@COMP0051:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
```

Here's a bit of my /var/log/Xorg.0.log:

```
[  1692.100] (II) Loading extension DRI2
[  1692.100] (==) Matched vesa as autoconfigured driver 0
[  1692.100] (==) Matched fbdev as autoconfigured driver 1
[  1692.100] (==) Assigned the driver to the xf86ConfigLayout
[  1692.100] (II) LoadModule: "vesa"
[  1692.100] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so

```

---

### Post by feed5000 on 2011-04-25
Some information on one of the computers that does recognise the Acer monitor.

```
guest2@COMP0050:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

```

Here's the same section of the /var/log/Xorg.0.log:

```
[    22.374] (II) Loading extension DRI2
[    22.374] (==) Matched intel as autoconfigured driver 0
[    22.374] (==) Matched vesa as autoconfigured driver 1
[    22.374] (==) Matched fbdev as autoconfigured driver 2
[    22.374] (==) Assigned the driver to the xf86ConfigLayout
[    22.374] (II) LoadModule: "intel"
[    22.374] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
```

---

### Post by feed5000 on 2011-04-25
So I do I get my systems with "unknown" monitors to recognise the intel chipset, instead of falling back to VESA?

---

### Post by feed5000 on 2011-04-26
So I figured out what it was. There's a [bug in X for the Brookdale chips]("https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus").

The four computers that weren't working, although they were different models, all used Brookdale for graphics. So Ubuntu defaults to the fbdev driver, instead of using the Intel (which crashes in some cases).

Some options are presented in the document linked above.

---

