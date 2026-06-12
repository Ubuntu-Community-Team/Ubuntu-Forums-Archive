---
title: "[SOLVED] video driver not working sony vaio SR290"
date: 2008-11-29
forum: Hardware
---

### Post by chex_m8 on 2008-11-29
I can't seem to get my video card working. any help would be greatly appreciated.
output of lspci:
  lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

xorg.conf file:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
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

### Post by NotoriousMOK on 2008-12-03
Have you tried changing;

this;
```
Driver "vesa"
```


to this;
```
Driver "intel"
```

---

### Post by chex_m8 on 2009-01-10
If you have a vaio with video driver issues you can go to this LINK and follow the directions. Ubuntu wasn't recognizing the intel driver until I did what what the [LINK]("http://ubuntuforums.org/showthread.php?t=1023801") says to do. GL

---

