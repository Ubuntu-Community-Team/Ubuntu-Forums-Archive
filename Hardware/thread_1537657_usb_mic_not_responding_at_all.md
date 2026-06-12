---
title: "usb mic not responding at all"
date: 2010-07-23
forum: Hardware
---

### Post by ldraptor on 2010-07-23
I'm new to ubuntu and i just installed skype recently but my usb mic is not responding at all. Ive looked around for ways to fix it but what I've tried so fare dos not work at all the input options in sound preferences do nothing. I'm also not rely sere what version i have but i dont know how to find out.

I'm using 32-bit on a HP Pavilion a1410y

---

### Post by lidex on 2010-07-25
Make sure the mic is plugged in.
Can you post the output of these terminal commands for me please:
```
uname -a
lsusb
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

