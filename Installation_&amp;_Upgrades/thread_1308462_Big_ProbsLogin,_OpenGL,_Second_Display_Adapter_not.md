---
title: "Big Probs:Login, OpenGL, Second Display Adapter not working"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by laserbeak43 on 2009-10-31
Hello,
I installed Jaunty the other day. I had to take my NVidia GeForce 8400 GS card out cause the install disk would not fully boot. So, after removing this, everything installed fine. So i installed a videogame and i couldn't play it cause there were no OpenGL drivers for my intel card. I googled around and found some fix stating that my card  fell victim to some bugs in the Jaunty relase. I tried the fix but it caused more problems than actualy fixing it. so then I figured i'd try and install my nvidia drivers. I downloaded drivers from the repo that supported my card's model number but they said i hadn't run nvidia-xconfig but doing this did nothing anyway. 

oh here's my card list.
```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)

```

so i decide to upgrade to karmic, hoping this would fix the problem, but now i can't even log into my account and have to use another account just to use the PC. I don't get an authentication error when logging in and can actually login to an xterm session just not an xsession. I use xfce.
can someone please help?

Thanks

---

### Post by laserbeak43 on 2009-10-31
my xorg.conf
> 
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


---

### Post by laserbeak43 on 2009-11-01
bump.
(wow there are so many people needing help these days and it's so hard to get ANY attention)

---

### Post by laserbeak43 on 2009-11-04
bump

---

### Post by laserbeak43 on 2009-11-10
bump

---

