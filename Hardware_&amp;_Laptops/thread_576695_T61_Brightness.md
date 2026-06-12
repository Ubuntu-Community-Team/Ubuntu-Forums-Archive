---
title: "T61 Brightness"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by cached on 2007-10-15
I'm having trouble increasing the brightness of the screen on a Thinkpad T61. When I try to use xbacklight (as per multiple sources online), it tells me that "No outputs have backlight property".

echo "level 7" >/proc/acpi/ibm/brightness doesn't work either.

What should I do? It's very difficult to work with a dim screen.

---

### Post by fabiovh on 2007-10-16
Hi! You can switch to a terminal (CTRL+ALT+F1), change the brightness, and them switch back to X (CTRL+ALT+F7).

Enjoy.

Fabiovh

---

### Post by cymacyma on 2007-10-16
You can use brightness control with virtual terminal. but It was reported that when you turn back to X, screen gonna black with nVidia Qudro series

---

