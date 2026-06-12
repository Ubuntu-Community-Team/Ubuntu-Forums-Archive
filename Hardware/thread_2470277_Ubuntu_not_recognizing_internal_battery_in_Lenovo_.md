---
title: "Ubuntu not recognizing internal battery in Lenovo x260"
date: 2021-12-23
forum: Hardware
---

### Post by dboland on 2021-12-23
My Lenovo x260 has a dual battery system. 

Both batteries were dected and charging in Windows when I first got it, after moving to Ubuntu it only detects the external battery.

Output from Upower shows this.

[TABLE="width: 500"]
[TR]
[TD]$ upower -e
/org/freedesktop/UPower/devices/line_power_AC
/org/freedesktop/UPower/devices/battery_BAT1
/org/freedesktop/UPower/devices/DisplayDevice[/TD]
[/TR]
[/TABLE]

Is there anything I can do to get Ubuntu to detect my internal battery?

---

