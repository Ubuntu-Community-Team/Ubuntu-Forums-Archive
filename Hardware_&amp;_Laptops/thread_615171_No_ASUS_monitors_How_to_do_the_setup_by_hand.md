---
title: "No ASUS monitors? How to do the setup by hand?"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by php_penguin on 2007-11-16
Hi there,

I have bought an Asus VW192G monitor (19" widescreen in other terms), but in the screens+resolutions list I don't have ASUS listed as an available manufacturer.

This isn't a huge problem, as the monitor still work, but unfortunately Ubu doesn't give me the right options for screen refresh, which is causing the monitor to make a damned annoying high-pitched noise all the *****ing time.

Anyway, my question was twofold:
1 - is there a way to get proper Asus support in this section? Any kind souls out there?
2 - is there a way to force the refresh rate to a proper selection?

For what its worth, the natural resolution is 1440x900, with refresh rates of 50Hz or 60Hz listed as normal.

Thanks in advance y'all!

---

### Post by taurus on 2007-11-16
Boot into recovery mode from GRUB menu and reconfigure your X server again with

```
dpkg-reconfigure -phigh xserver-xorg
```
When done, reboot with

```
shutdown -r now
```

---

