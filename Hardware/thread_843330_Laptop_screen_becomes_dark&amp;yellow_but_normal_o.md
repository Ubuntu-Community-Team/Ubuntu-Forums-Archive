---
title: "Laptop screen becomes dark&amp;yellow but normal on vista"
date: 2008-06-28
forum: Hardware
---

### Post by Olnex on 2008-06-28
After using Ubuntu for several months, my laptop's screen becomes dark and yellow, then I changed to vista, it is still dark and yellow, so I tried to adjust brightness in NVidia's setting panel, it does not help.
Then one day my laptop's screen become black, but I know the system (vista) is running, so I pressed the power button to force it shut down, then I restart again, the screen becomes normal white.
So I wonder is there a way to get information about display under vista and apply it to ubuntu?

---

### Post by prshah on 2008-06-28
> **Olnex said:**
> After using Ubuntu for several months, my laptop's screen becomes dark and yellow, then I changed to vista, it is still dark and yellow, 
restart again, the screen becomes normal white.




Looks to me like your display is failing; that said, try correcting the gamma: Open a terminal (Applications-Accessories-Terminal), then give the following command ```

sudo gedit /etc/X11/xorg.conf

```

Find a section similar to the below: (Note that the values and settings below are examples, your values/settings may be different/missing.)

> Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Samsung"
	Horizsync	xx-xx
	Vertrefresh	xx-xxx
EndSection

and, before the endsection line, add a single line as below:```
	Gamma	1.0
``` so that the new part reads as ```

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Samsung"
	Horizsync	xx-xx
	Vertrefresh	xx-xxx
	[color=red]Gamma	1.0[/color]
EndSection
```

Save, and close the editor, logout, restart X server with Ctrl+Alt+BkSpace.

Any improvement? If it is too bright, reduce the gamme from 1.0 to 0.75 or so on, you will have to experiment to find the correct setting.

Caveat: Nothing here should be harmful to the monitor, but to be on the safe side (Considering that I think your monitor/display is failing anyway): Disclaimer- your mileage may vary, I cannot be held responsible for any problems any info here may or may seem to cause.

---

### Post by AlexBellisBrown on 2008-06-28
System - Preferences - Screen Resolution. Check if its on 60Hz, if not, try changing it to 50Hz.

---

