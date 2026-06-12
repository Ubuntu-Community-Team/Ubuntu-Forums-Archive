---
title: "Brightness Doesn't Change HP DV6"
date: 2012-06-12
forum: Hardware
---

### Post by caeso on 2012-06-12
I have an HP dv6.

I am trying to change the brightness on the screen.

The brightness keys work (meaning it changes the brightness slider), and I can verify that the brightness integer in
```
/sys/class/backlight/acpi_video0/backlight
```
and
```
/sys/class/backlight/acpi_video1/backlight
```
changes from 0 to 10.

However, there is no physical change on my monitor.

Could it have something to do with this laptop having 2 GPUs (an Intel and AMD)?

Any help would be appreciated. Thanks!

---

### Post by alex.stapleton on 2012-06-12
I believe there are some issues with the backlight in the Intel drivers at the moment. The xorg-edgers ppa might help (although it didn't for me.)

---

