---
title: "Anyone know anything about i8k?"
date: 2008-06-03
forum: Hardware
---

### Post by mjskia1 on 2008-06-03
Does anyone have any experience with the i8k kernel module (from the i8kutils package)?  It's supposed to support special hardware settings on Dell laptops, but I've had nothing but trouble with mine.  I tried installing the package so I could use the fans and the volume buttons (Fn+PgUp/PgDn) on my laptop.  Unfortunately, whenever I enable the kernel module, I completely lose my keyboard, touchpad, and trackpoint nubbin thing.  Google's not been too helpful -- has anyone seen/fixed this before?

Here's what I'm running:
Dell Latitude C610
Kubuntu 8.04 32-bit (upgraded from a 7.10 install with the same problem)
Kernel 2.6.24-17-generic (according to uname -a)

Whenever I perform ```
sudo modprobe i8k
```, I lose all input from what's on the laptop.  The USB port (yes, one, the laptop's old) still works, so I can use a USB mouse (when I have one).  But right now I'm faced with a choice between having keyboard and having fans, so I'm not too thrilled about that.

Any help is appreciated.

---

