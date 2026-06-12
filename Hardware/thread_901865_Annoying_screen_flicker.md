---
title: "Annoying screen flicker"
date: 2008-08-26
forum: Hardware
---

### Post by AngryNapkin on 2008-08-26
I'm running Ubuntu on an HP dv9000. The screen flickers sometimes which is distracting and annoying. If I go to system-->Admin-->hardware drivers I get a statement that reads, "Proprietary drivers are being used to make this computer work properly". Under device driver reads "NVIDIA accelerated graphics driver (latest cards), enabled and in use. I'm sure if this is the correct driver I should be using, or if my problem lies elsewhere.

---

### Post by kerry_s on 2008-08-26
you probably need to adjust you refresh rate.

---

### Post by AngryNapkin on 2008-08-27
Only option I'm presented with is 50hz

---

### Post by kerry_s on 2008-08-27
> **AngryNapkin said:**
> Only option I'm presented with is 50hz

then you need to put a wider options in your xorg.conf, look up what your screen runs at, my screen has a info button that tells me on the front.

use-> gksu gedit /etc/X11/xorg.conf

then add your stuff to the monitor section, mine looks like this:

```
Section "Monitor"
	Identifier	"S/M 955DF"
	Option		"DPMS"
[B]        HorizSync       30-85
        VertRefresh     50-160[/B]
EndSection
```

---

### Post by AngryNapkin on 2008-08-28
I found the option in the nvidia settings, but when I try to merge into the config file I get the following error:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

---

### Post by kerry_s on 2008-08-28
> **AngryNapkin said:**
> I found the option in the nvidia settings, but when I try to merge into the config file I get the following error:

Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

run nvidia-settings as root.

---

### Post by AngryNapkin on 2008-08-28
Alright thanks. I now have two options: 73hz and 50hz. Unless I'm mistaken, the display on an hp dv9000 should be running at 60hz. This is what my config file now reads:

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LPL"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

```

Also, under nvidia-settings, I can set my refresh rate to 60hz. However, if I go to system-->preferences-->screen resolution, I am presented with on 50 and 73hz options. I assume this setting box is what dictates which refresh rate my machine runs, in effect overruling whatever setting change I make in nvidia-settings.

---

### Post by kerry_s on 2008-08-28
> **AngryNapkin said:**
> Alright thanks. I now have two options: 73hz and 50hz. Unless I'm mistaken, the display on an hp dv9000 should be running at 60hz. This is what my config file now reads:

```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LPL"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

```

Also, under nvidia-settings, I can set my refresh rate to 60hz. However, if I go to system-->preferences-->screen resolution, I am presented with on 50 and 73hz options. I assume this setting box is what dictates which refresh rate my machine runs, in effect overruling whatever setting change I make in nvidia-settings.


i think you have this bug-> [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/92599](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/92599)

so a couple of things to try:

sudo nvidia-xconfig

and/or try putting:
Option "DynamicTwinView" "false"

in the device section

---

