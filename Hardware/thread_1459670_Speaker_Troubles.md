---
title: "Speaker Troubles"
date: 2010-04-21
forum: Hardware
---

### Post by schnide on 2010-04-21
So I recently installed Ubuntu on my HP Pavilion Dv7 laptop.

Most everything is going smoothly except that I am unsure how to get my built-in sub woofer, to work. 

If anyone has any idea on this I would greatly appreciate it!

I'm running 64-bit

Thanks

---

### Post by lidex on 2010-04-22
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

