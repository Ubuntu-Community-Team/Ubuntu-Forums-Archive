---
title: "RAM upgrade - not recongnized by Ubuntu"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by dretep on 2005-08-04
I've done a few searches here and on Google without any luck.  I had my RAM upgraded from 1GB to 2GB today and Ubuntu does not recognize it.  Any ideas or suggestions would be appreciated.

- pd -

---

### Post by maruchan on 2005-08-04
Are you using the 686 kernel?

---

### Post by az on 2005-08-04
Check what kind of processor you are using and switch your nerle to match it (686 is for intel, k7 is for amd smp is for dual or multiple intel processors...)

---

### Post by dretep on 2005-08-05
[QUOTE=maruchan]Are you using the 686 kernel?[/QUOTE]

I am now, thanks!

---

### Post by magm58 on 2005-08-05
[QUOTE=dretep]I am now, thanks![/QUOTE]
please i have the same ploblem how you select the 686 kenneel

---

### Post by jeremy on 2005-08-06
[QUOTE=magm58]please i have the same ploblem how you select the 686 kenneel[/QUOTE]
 The easiest way is to use synaptic, and select, in this case, linux-image-2.6.10-5-686

---

### Post by ilmw on 2005-08-06
[QUOTE=magm58]please i have the same ploblem how you select the 686 kenneel[/QUOTE]
[see this thread](http://ubuntuforums.org/showthread.php?t=53990)

---

### Post by Sephiriz on 2005-08-06
Are there any other differences between the 386 and 686 kernel aside from RAM capabilities?  I'm simply wondering because I was using the 386 until now, and ndiswrapper worked just fine, but when I tried using the 686 instead, I got a fatal error with ndiswrapper.  Anybody know why?

---

