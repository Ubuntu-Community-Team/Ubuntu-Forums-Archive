---
title: "Can't Get Dual Monitor In 10.04"
date: 2011-04-04
forum: Hardware
---

### Post by duffboy on 2011-04-04
I recently upgraded from Intrepid to Lucid. I actually did a fresh install on my old Dell 710m.

I had to play a bit with my display settings and wound up using an xorg.conf file since the new display couldn't figure my system out.

I am trying to hook up my second monitor without any luck. It worked like a charm in Intrepid, but if I even boot with it plugged in I get a black screen as X loads.

Any help is appreciated, here are my configurations.

Current (working) xorg.conf to display on my notebook.
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Old, Ubuntu 8.10 dual head xorg.conf.
```
Section "Device"
        Identifier      "Configured Video Device"
        Option          "monitor-LVDS" "12Screen"
	Option          "monitor-VGA" "19Monitor"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
	Option "PreferredMode"  "1280x800"
	Option "Position" "900 0"
EndSection

Section "Monitor"
        Identifier      "19Monitor"
        Option "LeftOf" "Configured Monitor"
	Option "PreferredMode"  "1440x900"
        Option "Enable"  "true"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
	SubSection "Display"
		Virtual	2180 2240
	EndSubSection
EndSection
```

Thanks,
Dave

---

