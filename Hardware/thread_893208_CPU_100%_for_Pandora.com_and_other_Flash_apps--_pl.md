---
title: "CPU 100% for Pandora.com and other Flash apps-- please help!"
date: 2008-08-18
forum: Hardware
---

### Post by feigelman on 2008-08-18
Hello, I'm trying to figure out why my computer locks up and becomes unresponsive whenever viewing Pandora.com, or other flash applications.  It doesn't crash, it just plays jarringly, sort of in bursts.  I have tried using firefox 3, firefox 2, Opera, and epiphany and all create the same problem.  I have tried the non-free flash player versions 9.124, and the 10-beta, with the same results.

I have a 3.2 GHz AMD, 2 GB ram, so it's not a problem of my computer simply being "too slow."  The internet connection is wireless, but it is fast enough for Pandora to stream seamlessly when booted into Windows, or on other machines on the same wireless AP.

I've also tried disabling visual effects, etc., to try to reduce the load on the CPU but the result is always the same when viewing flash apps.

Running Hardy 8.04.

Please help!

---

### Post by kerry_s on 2008-08-18
what is your video card?

---

### Post by feigelman on 2008-08-18
> **kerry_s said:**
> what is your video card?

ATI Radeon X1300.  Using restricted-driver fglrx, and everything seems to be working.  Getting good FPS on openGL apps, etc, and Compiz seems to be working fine when I'm not using flash apps.  Disabling compiz doesn't help, either.

---

### Post by kerry_s on 2008-08-18
i bet it's that dri bug, try disabling dri:
```
option "no_dri" "yes"
```

it will disable 3d, so i hope you don't have compiz on, see how it is without.

---

