---
title: "my Dell Latitude D630 cannot run xrandr after upgrading to 8.10"
date: 2008-11-20
forum: Hardware
---

### Post by syn4k on 2008-11-20
After I upgraded from 7.10 to 8.10 my xrandr will not run.
I always sign in, and run this command:
```
xrandr --output LVDS --auto --output VGA --auto --left-of LVDS
``` which always gets my settings going just fine...

Now however, when I run this command I get the output:
> xrandr: screen cannot be larger than 2560x800 (desired size 2640x800)

However, my config file already defines the correct virtual size so this should not be an issue.
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600"
		Virtual 2560 800
	EndSubSection
EndSection
```

help?

---

