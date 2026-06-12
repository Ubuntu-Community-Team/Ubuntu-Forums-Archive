---
title: "WOW / WINE / Mobile 915GM/GMS/910GML Express - PLEASE HELP!"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by kruupy on 2007-06-18
Hi all,

I am having severe problems with my laptop when playing world of warcraft. My Laptop specs are:

Travel Mate 4060
2 GHZ cpu
1 GB DDR Ram
Mobile 915GM/GMS/910GML Express

when I had windows xp installed wow,graphically worked fine, however it started to blue screen at random times - which lead me to install ubuntu in the hopes that it wouldnt blue screen and die.

I am able to play wow on ubuntu through hours of reading tutorials and configurations however it is noooo where near  the speed of when I was playing it in windows, I even have to set the rendering distance to absolute minimum which is unbearable.

What I am wondering is whether this is an issue with wine (perhaps cedegar is faster? - I tried it with crossover but received the same results)  or whether it is a graphics card driver problem (which seems to me to probably be the issue)

currently I am using the i810 drivers, I noticed that the intel drivers (higher version drivers)are available but when I install them the game doesnt run at all - in fact when i try to run wine ubuntu logs me off!?! - apparently people have had similar problems with the intel x.org drivers aswell.

Can anyone help me? I seriously beg im an addict of wow and am slowly dying day by day from withdrawal symptoms.....

Thanks all,
From Kruupy.

Ps. glxgears gives me 915 FPS - ive been reading that there are some other linux distros that can provide higher frame rates such as Mandriva? - but is there a free distro that provides the same results as mandriva?

---

### Post by Syke on 2007-06-18
Have you tweak wow to use opengl, either in the config.wtf or running from the command line like this:

```
wine WoW.exe -opengl
```

---

### Post by Jim March on 2007-06-18
I'm going to assume you've got more than 512megs RAM here.  This is what the devices section of my xorg.conf looks like - notice the setting for amount of video RAM at 128megs:

---
Section "Device"
	Identifier "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver "i810"
	BusID "PCI:0:2:0"
	Option "XAANoOffscreenPixmaps" # added for Beryl
	VideoRam        128000
EndSection
---

I suspect that's an issue.

---

