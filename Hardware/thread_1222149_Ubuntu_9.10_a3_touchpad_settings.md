---
title: "Ubuntu 9.10 a3 touchpad settings"
date: 2009-07-24
forum: Hardware
---

### Post by junke1990 on 2009-07-24
Hey People

I've just run my updates from 9.10 but after reboot my touchpad isn't working properly anymore.

I installed the app to configure the touchpad but I cant change the setting from single too two finger scrolling here. Where can I edit this? I looked in the xorg.conf but there isn't anything in there about the touchpad settings.... I'm running on a Asus eee 1000h.

for the rest of the alpha's, keep up the good work!

---

### Post by ZaHACKieL on 2009-07-24
You mean two finger scrolling like in the macs?

ZL

---

### Post by junke1990 on 2009-07-25
exactly... cant find the setting or config file anywhere

---

### Post by ZaHACKieL on 2009-07-27
> **junke1990 said:**
> exactly... cant find the setting or config file anywhere

I think you may find the wat to get the config file in this thread:

[http://ubuntuforums.org/showthread.php?t=516798](http://ubuntuforums.org/showthread.php?t=516798)

let me know if you get it

ZL

---

### Post by junke1990 on 2009-07-30
Been looking through the posts and got to the conclusion that I need the following "setting" edited.

```

        Option          "VertTwoFingerScroll"   "1"
        Option          "HorizTwoFingerScroll"  "1"

```

if I run **synclient -l** I can  see that both options are 0, reading on in the posts I see that I need to add the above lines to xorg.conf . My question is where or how? I don't have the device/touchpad in there. The settings must be stored somewhere but where?

my entire xorg.conf (without the comments above it)
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2048 768
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

---

