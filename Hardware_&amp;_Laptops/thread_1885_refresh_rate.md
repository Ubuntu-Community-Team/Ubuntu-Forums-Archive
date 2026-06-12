---
title: "refresh rate"
date: 2004-10-24
forum: Hardware &amp; Laptops
---

### Post by riggits on 2004-10-24
How can I change the refresh rate of my monitor???  I have used the Computer/System Preferences/Screen Resolution application, but the only refresh rate that I can select is 60Hz.  The monitor supports many other rates, yet it is not possible to change to another value.

Any advice is appreciated :)

---

### Post by Dracontopes on 2004-10-24
You have to set your Horizontal and Vertical Refreshrate for your monitor in the XF86Config-4 file, which is located in etc/X11/

It's in the [Monitor] section I think. When you set those up correctly, X will set a nice refreshrate automatically. When you are not satisfied with that refreshrate, you must add some ModeLines to the XF86Config-4 file, on google you can find some generators which will generate those lines.

Good luck!

---

### Post by jdong on 2004-10-24
Example /etc/X11/XF86Config-4:
```

Section "Monitor"
	Identifier	"VL 1716"
	HorizSync	31-64
	VertRefresh	60-60
	Option		"DPMS"
EndSection

```

the VertRefresh tag is what you want to change. It's usually specified as a range, as shown.

---

