---
title: "Lenovo T410 backlight brightness issue"
date: 2010-12-24
forum: Hardware
---

### Post by liambowen on 2010-12-24
Hello everyone

I recently installed Ubuntu 10.10 after using 10.04 prior to a hard drive crash.  In general, I'd say that both versions work very well, but I have one very annoying issue.  When I start up the system, the backlight is stuck at one (seemingly random) backlight brightness setting and adjusting the backlight brightness using the keys does nothing, although I can see the "progress bar" indicator in the upper right corner move.  This has happened in 10.04 and 10.10.

Strangely, I've experienced none of the other issues I was able to find, including one related to printing and one related to the wireless driver.

I'm not sure if the graphics card has anything to do with this, but I am using the NVIDIA proprietary drivers.  Any insight would be greatly appreciated.

---

### Post by liambowen on 2010-12-24
So everything is fixed by changing:
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```
to
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset acpi_backlight=vendor"
```
in
```
/etc/default/grub
```

Except that now the brightness adjustment keys don't actually adjust anything, but at least it's always at max brightness.  Good enough!

---

