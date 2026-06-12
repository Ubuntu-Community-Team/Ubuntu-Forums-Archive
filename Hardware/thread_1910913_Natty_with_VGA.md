---
title: "Natty with VGA"
date: 2012-01-18
forum: Hardware
---

### Post by geekman2 on 2012-01-18
I have an hp Pavilion dv2000 with natty narwhal and I want it to work with a hp vga monitor. I've tried plugging it in, but it doesn't see it

---

### Post by geekman2 on 2012-01-19
Does anybody know how to this? I'm probably just overlooking something really obvious
thanks for your help

---

### Post by madvinegar on 2012-01-19
Run the usual tests.

Plug it in and run in terminal ```
lsusb
``` and post the results.

Also, unplug it, run in terminal ```
sudo dmesg -c
``` and then plug it in again and run ```
dmesg
``` and post the results.

---

### Post by grahammechanical on 2012-01-19
It is a laptop, yes? Does this mean that you have to press an Fn key to switch to the VGA port? What does the user manual say about using the VGA port?

Are you using a proprietary video drvier? That should come with its own configuration settings manager. Does it give you an option to detect displays?

Regards.

---

### Post by madvinegar on 2012-01-19
Nice thought Graham. In laptops it is usually Fn+F1.

---

