---
title: "Intrepid and the dreaded ATI IGP 320 (U1)"
date: 2009-02-03
forum: Hardware
---

### Post by crho85 on 2009-02-03
I recently installed Intrepid onto my HP ZE4300 laptop.I am running an XP Intrepid dual boot (intrepid was installed 02-02-09) All went smoothly until I started up. The screen resolution was too high and I could not see the whole screen. Nothing was listed under screen resolutions. I knew right away that this was caused by the dreaded ATI Radeon Mobilty IGP 320M (AKA U1). In order to do anything I installed the ATI driver with EnvyNG. Now I am running but in low graphics mode.

Here is the xorg file.

```
Code:

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
```

As you see it is not saying much. the lspci -nn | grep VGA reports the correct card.

I found [_[COLOR="Red"]this page[/COLOR]_]("https://help.ubuntu.com/community/RadeonDriver")

Will this work for me. If not could someone please help me out, I am still pretty new to the ubu .

---

