---
title: "Keyboard Backlight for Toshiba Satellite P755 S5182"
date: 2014-08-05
forum: Hardware
---

### Post by josephj on 2014-08-05
I have a Toshiba Satellite P755 S5182 notebook. Everything works great (just upgraded to Kubuntu 14.04.1) except for the keyboard backlight - which works fine in Windows 7 (dual boot - for when I'm feeling masochistic).

So far, I've figured out it has something to do with acpi, but that's about it.

I thought I saw a post somewhere about needing a newer kernel than the one I had in 12.04 (3.2.x) and that 3.10 would help. 14.04 has 3.13, but I can't seem to find that post now.

The backlight key (FN-Z) shows up properly in xev.

I can provide any additional information if needed.

There's a row of capacitive buttons above the keyboard. Most of them work fine. The one with a curved arrow in a square does nothing I'm aware of. (I saw a post somewhere that said it was related to the keyboard backlight in Windows.)

Any help with this would be greatly appreciated. I often use it in low light conditions and really need the keyboard backlight to see the keys.

---

### Post by jeremy31 on 2014-08-05
```
 for i in /sys/class/leds/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done   
```
It might be /sys/class/led but one of them should have the backlight control for the keyboard and it may not work like it does in win7

---

