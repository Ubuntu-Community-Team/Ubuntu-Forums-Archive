---
title: "Radeon 9800 Pro (fglrx) not working: AGP failed to initialize"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by matthias_k on 2007-04-22
Hi,

today I wanted to check out how well the new proprietary driver manager works and used it to install the ATI proprietary driver module (fglrx). Installation went fine, I was prompted to reboot, but after the restart my screen went black and didn't recover. I switched to the console and checked the X11 logs, and it seems that the driver failed to initialize the AGP:

```

 matthias:.config$ cat /var/log/Xorg.0.log.old | grep \(EE\)
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) fglrx(0): [agp] unable to acquire AGP, error "xf86_ENODEV"
(EE) fglrx(0): cannot init AGP
(EE) AIGLX: Screen 0 is not DRI capable
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom

```
xf86?! That sounds a lot like XFree86, but I'm using X.org of course. Anyway, it obviously doesn't work and the other support threads didn't help. I also followed the instructions [here](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide), but no luck.

Any ideas? The card worked fine with Dapper.

---

### Post by matthias_k on 2007-04-23
bump

---

