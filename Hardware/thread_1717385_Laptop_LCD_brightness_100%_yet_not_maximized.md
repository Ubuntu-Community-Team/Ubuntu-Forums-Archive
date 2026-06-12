---
title: "Laptop LCD brightness 100% yet not maximized"
date: 2011-03-29
forum: Hardware
---

### Post by d106550 on 2011-03-29
Hello guys. Here's an issue I'm having on my ASUS eee PC 1215N

Under Ubuntu the display brightness will not maximize to the maximum level possible on my particular LCD. I noticed this because I'm using both Windows and Ubuntu on the same laptop.

Under Windows the display is measurably brighter at full brightness setting as opposed to under Ubuntu. I've had this independently verified by two other people.

I'm not running the proprietary Nvidia ION drivers since they crash ubuntu during start-up. I would imagine this is a driver issue. I've verified this issue exists while on battery and while on AC power and both times the brightness setting was set to 100%.

Any thoughts?

---

### Post by roeldebacker on 2011-04-13
I have the same problem, but am also still in need of a fix for this.

---

### Post by rushingad on 2011-04-15
Ive noticed that my LCD will be max brightness in Ubuntu if it was at max brightness in Windows

---

### Post by panicpanda on 2011-05-01
This happens to me on my laptop too :3  I have to type the following into the terminal:

 sudo setpci -s 00:02.1 f4.b=ff

in order to reach maximum brightness.

---

### Post by colombo1980 on 2011-08-24
THANK YOU!!!! =D>

I've searching for a solution for several months now.
```
sudo setpci -s 00:02.1 f4.b=ff
```
did not work for me, but after i had a look at lspci:
```
$ lspci
[...]
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
[...]
```
I tried the other intel graphics device-thingy:
```
sudo setpci -s 00:02.0 f4.b=ff
```
and THAT did the trick.

Thanks again, I would never had solved this on my own. (Although I do have to find a way now to keep it permanent, i.e. after restart/suspend/changing the brightness etc...)

---

