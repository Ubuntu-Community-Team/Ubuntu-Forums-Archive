---
title: "vertical scroll region too big"
date: 2008-06-08
forum: Hardware
---

### Post by buccaneere on 2008-06-08
It's all in the title.

My zone for this control is about 1/3 of the field. How do I reduce it?

Thanks/buccaneere

---

### Post by buccaneere on 2008-06-09
The max value I could give to the cursor field rt edge coordinate is about 5900. 8176 takes away vertical scroll capability, as does any value over about 6100.

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
        Option          "RightEdge"             **[COLOR="Red"]"5900"[/COLOR]**
	Option		"HorizEdgeScroll"	"0"
        Option          "MaxTapTime"            "0"
        Option          "SHMConfig"             "1"
EndSection


 time . x . y . z . f . w . l . r . u . d . m . multi . gl . gm . gr . gdx . gdy
3.870 [COLOR="Red"]**8176**[/COLOR] 2999 12 1 4 0 0 0 0 0 00000000 0 0 0 0 0
3.937 **[COLOR="Red"]8176[/COLOR]** 2963 20 1 4 0 0 0 0 0 00000000 0 0 0 0 0
3.952 [COLOR="Red"]**8176**[/COLOR] 2968 21 1 4 0 0 0 0 0 00000000 0 0 0 0 0


Anybody???

---

