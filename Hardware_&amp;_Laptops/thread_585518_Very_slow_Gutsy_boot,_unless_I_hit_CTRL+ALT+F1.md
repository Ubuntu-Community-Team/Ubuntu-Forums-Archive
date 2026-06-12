---
title: "Very slow Gutsy boot, unless I hit CTRL+ALT+F1"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by styxie on 2007-10-21
When I boot Gutsy, it takes ages (a lot more than Feisty, which I also installed) to load. But when I hit CTRL+ALT+F1, it loads quickly. When I hit CTRL+ALT+F1 after a few minutes during the normal slow booting, it says:

FWH not detected

Among other things, but this is the only thing I could record. Also, I don't see the Ubuntu logo and the orange loading bar. The screen is totally black (not turned off, just plain black). What should I do?

---

### Post by max_power on 2007-10-31
I have the same problem. I have not tried using ctrl+alt+f1 but i will on next reboot.

here is some more info from my side:

i can boot into safe graphics mode and it only takes about 30 seconds. the weird thing is when i boot into safe mode, then exit graphics mode (CTRL+ALT+ BACKSPACE) and at command line enter # exit

the system logs into the GDM and i can log in and everything is fine.

?????????????????

compaq presario v5000 (laptop)
ati radeon 200m graphics 
AMP Sempron

---

### Post by jellymaster2 on 2007-10-31
> **styxie said:**
>  Also, I don't see the Ubuntu logo and the orange loading bar. The screen is totally black (not turned off, just plain black). What should I do?

Well on an older computer when I tested an install of Ubuntu 7.04 Feisty(This computer was running a radeon 9250 graphics card which I also use in my computer now and works nicely with Ubuntu)there was a problem with the graphics card drivers and doing anything while not on the onboard(Asus motherboard forgot the onboard specs but were horrible)u couldn't run windows but if I popped in the Live CD and just let it sit on the Radeon it would eventually pop up but other than that it was black. So it's possible that your graphics cards drivers are not working properly.

---

