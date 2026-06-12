---
title: "Power Problem"
date: 2011-01-24
forum: Hardware
---

### Post by mogwai on 2011-01-24
Ubuntu will not boot unless the AC power is disconnected and the laptop is running on battery. Otherwise I end up with a blank screen with a blinking cursor just after selecting from grub. Alt-SysReq REISUB has no effect.

I have had this bug on 10.04 for a while, then when I re-installed and it left. But it is back. I think the problem lies around booting Ubuntu while on battery(?). I usually have it plugged in most of the time.

If I use acpi=off on the kernel line my system runs quite slow and my mouse (Logitech Wireless Laser Notebook Mouse) jerks around, but when I use the touchpad it is smooth. Oh, yeah - and it boots while on AC power.

I am using 10.10 on a Thinkpad R61. Any ideas?

---

### Post by mogwai on 2011-03-02
bump

---

### Post by mogwai on 2011-03-03
It appears to be fixed with a recent kernel update (2.6.35-27.48).

---

