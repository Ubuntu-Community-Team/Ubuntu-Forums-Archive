---
title: "Ati Radeon HD 3400 Series"
date: 2009-04-05
forum: Hardware
---

### Post by igurbev on 2009-04-05
Hi,
I am having Asus M51Sseries with Ati Radeon HD 3400 and trying to install open source ati driver (because fglrx do not work for me at all). But x server doesn't start:
```
(EE) RADEON(0): Unable to map FB aperture. No such file or directory (2)

Fatal server error:
AddScreen/ScreenInit failed for driver 0
```

What can I do?

---

### Post by igurbev on 2009-04-13
I tried new binary ati driver(again) yesterday and get this:

```
(II) LoadModule: "fglrx"

(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
dlopen: /usr/lib/xorg/modules/drivers//fglrx_drv.so: undefined symbol: miZeroLineScreenIndex
(EE) Failed to load /usr/lib/xorg/modules/drivers//fglrx_drv.so
```

I think ATI video card is really bad choice.

---

