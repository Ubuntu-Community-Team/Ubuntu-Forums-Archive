---
title: "problems with my graphic card"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by MonsterCake on 2007-09-25
hi, I have an onboard Via graphic card (with 128mbs), but it acts really weird. In /etc/X11/xorg.conf, its set to use vesa drivers, but when I set it to use Via drivers, X11 doesn't even start.

But anyway, using the vesa drivers, I can't get composite managers to work (I'm trying to use compiz btw). I only get a whit screen. and the same thing happens with Beryl. I've tried a couple of drivers, but they didn't helped at all.
My motherboard is a Biostar P4M800-M7.
if anyone that has the same hardware and problem then I, can they tell me how they fixed it?

Also, if I can't get it to work, I might buy a nVidia card. (PS: also tell me what nVidea models are more supported ;) )

---

### Post by pay on 2007-09-25
Try ```
sudo apt-get install xserver-xorg-video-via
```I'm not sure if they are installed as default because i don't have that card. Then change to the via driver ```
sudo cp /etc/X11/xorg/conf /etc/X11/xorg/conf_bak
sudo nano /etc/X11/xorg.conf
```Then go to Section "Device" and change driver to via. Add > Section "DRI"
	Mode	0666
EndSectionto the end of the file.

---

### Post by MonsterCake on 2007-09-25
I already have xserver-xorg-video-via installed.
In the "Device" section of xorg, X11 won't start with "via" (I think I've already say that)
and I already have that code in Xorg:
```
Section "DRI"
        Mode    0666
EndSection

```

well, I've been searching like a mad on google for drivers. I think I don't have any choice but getting a new graphic card :(

---

### Post by reckless2k2 on 2007-09-25
there is a via tutorial about compiling direct from the source site. i never got it to work right with my onboard via though and just forked out some cash for a nvidia card. the 7000 line seems to work fine on ubuntu. i think 8000 line might give some problems.

---

### Post by MonsterCake on 2007-09-26
> **reckless2k2 said:**
> there is a via tutorial about compiling direct from the source site. i never got it to work right with my onboard via though and just forked out some cash for a nvidia card. the 7000 line seems to work fine on ubuntu. i think 8000 line might give some problems.

ok, thanks for the info

---

