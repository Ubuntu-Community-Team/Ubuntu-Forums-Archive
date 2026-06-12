---
title: "Hang during boot - nolapic_timer problems."
date: 2010-10-15
forum: Hardware
---

### Post by Glaucous on 2010-10-15
I'm having a problem that one out of four times, kernel boot freezes, this often occurs at: 
```
[    6.626865] ata2: softreset failed (device not ready)
[    6.626972] ata2: applying SB600 PMP SRST workaround and retrying
```

My system:
GA-MA790X-UD3P (AMD SB750, apparently known for some incompatibility). 
AMD Phenom 2 x4 940
NVIDIA GTX 260
Three harddrives, one Corsair SSD.
Ubuntu 2.6.35-22.34-generic 2.6.35.4

lspci -vv
[http://pastebin.ubuntu.com/513761/](http://pastebin.ubuntu.com/513761/)

But if I push the power button, then the boot continues. And often it occurs multiple times during the same boot. Please note though that everything except the boot works great.

When adding **nolapic_timer** to by boot parameters fixes all of this. I have never gotten any boot problems at all when using this parameter.
This does however seem to add some problems itself. Some OpenGL programs get very low FPS/performance, and some other applications as well (qjoypad when controlling mouse for instance). 

dmesg without nolapic_timer, did stop three times during boot.
[http://pastebin.ubuntu.com/513730/](http://pastebin.ubuntu.com/513730/)
Xorg log without nolapic_timer
[http://pastebin.ubuntu.com/513731/](http://pastebin.ubuntu.com/513731/)

dmesg with nolapic_timer, no problems during boot
[http://pastebin.ubuntu.com/513736/](http://pastebin.ubuntu.com/513736/)
Xorg log with nolapic_timer
[http://pastebin.ubuntu.com/513737/](http://pastebin.ubuntu.com/513737/)

When looking at the dmesg log you can see that boot is a lot faster with nolapic_timer, since it doesn't stop/hang.

---

