---
title: "How to increase the brightness of my laptop screen"
date: 2008-11-12
forum: Hardware
---

### Post by thangola on 2008-11-12
Hi everybody,
I have a problem with my laptop screen. The brightness is too dim. I've adjust to maximum value at the Brightness applet.
I'm using the HP 6530s laptop with Ubuntu 8.10.
Some another info about DD04:
```

~$ cat /proc/acpi/video/GFX0/DD04/brightness 
levels:  100 51 30 37 44 51 58 65 72 79 86 93 100
current: 100
~$ cat /proc/acpi/video/GFX0/DD04/info 
device_id:    0x0410
type:         UNKNOWN
known by bios: no
~$ cat /proc/acpi/video/GFX0/DD04/state 
state:     0x1d
query:     0x00
```
(The DD01 .. DD03, DD05's brightness files are 0 all).

Any idea?
Thanks for reading.

---

### Post by thangola on 2008-11-13
Is there anybody?

---

### Post by tvtech on 2008-11-13
duno if this will help in your case but this solved it on the asus m50/m70 laptops 

[http://ubuntuforums.org/showthread.php?t=973403](http://ubuntuforums.org/showthread.php?t=973403)

---

### Post by user-max on 2008-11-13
hm... I am currently running HP dv 2000 with Ubuntu 8.10 on it.. I see that your brightness level is at 100%... However, did u try just simply Fn + F8 ?  might be silly question but u never know.

---

### Post by thangola on 2008-11-13
> **tvtech said:**
> duno if this will help in your case but this solved it on the asus m50/m70 laptops 

[http://ubuntuforums.org/showthread.php?t=973403](http://ubuntuforums.org/showthread.php?t=973403)
Thanks for the relpy, but it's not my problem. My screen is too dim although my brightness level is 100% (maximum value).
Plz help me.

---

### Post by thangola on 2008-11-13
Anyone here?

---

### Post by Mardoct909 on 2008-11-13
Have you looked around for another place that might have a bar that's really low?

More than one I've had sound issues because my main mixer was maxed out but some other one was low.

---

### Post by thangola on 2008-11-13
But I cant find another place that allow me to adjust the brighness level.

---

### Post by DataMatrix on 2008-11-14
I have the same problem with an ASUS X71A notebook under 8.10, the bar showing brightness changes, but display stays at 100% brightness anyway.
Interestingly, on this notebook there is a button to turn off the backlight without turning the display off (in daylight, I can see the contents of the display) and it works just fine, both on 8.04, Vista Ultimate (it was preinstalled so i had to remove it), 8.10 and even in the bios setup. Any ideas?

---

