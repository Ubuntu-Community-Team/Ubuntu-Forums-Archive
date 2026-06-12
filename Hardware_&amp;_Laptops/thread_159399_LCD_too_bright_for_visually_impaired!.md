---
title: "LCD too bright for visually impaired!"
date: 2006-04-12
forum: Hardware &amp; Laptops
---

### Post by xyz on 2006-04-12
Hi-
I've just gotten through compiling the Vanilla kernel following 'RubenGonc's" great HowTo:[http://ubuntuforums.org/showthread.php?t=84174](http://ubuntuforums.org/showthread.php?t=84174). No problem!

Kernels .386 and .686 (which I still have in GRUB) were good to me because I could lower my Toshiba Satellite A40's brightness running:

```
 sudo echo "brightness:1" > /proc/acpi/toshiba/lcd

``` Brightness1 is what I need.Believe it or not, LCD's TOO bright for me!

Howerver, now with Vanilla 2.6.14, when running the same command,I get this:

> root@meander:~# sudo echo "brightness:1" > /proc/acpi/toshiba/lcd
bash: /proc/acpi/toshiba/lcd: No such file or directory


If somebody could help me on that one, my eyes would be most grateful!(n00b)

---

### Post by xyz on 2006-04-13
Just thinking...why don't I have a /proc/acpi file? kernel 2.6.24 compiled yesterday.
So how would I go about 'getting' /proc/acpi? No Power Management either.

---

