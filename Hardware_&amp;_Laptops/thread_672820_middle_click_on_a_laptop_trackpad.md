---
title: "middle click on a laptop trackpad"
date: 2008-01-20
forum: Hardware &amp; Laptops
---

### Post by gerfuls on 2008-01-20
i have a laptop with a trackpad and a left and right click buttons. how can i middle click (like click down the wheel for autoscroll)???

---

### Post by erfahren on 2008-01-20
what kind of trackpad (or touchpad) is it?

you can look at your /etc/X11/xorg.conf file to see its entry (you can just browse to that file and open it in the text editor - it'll open as read-only)

or you can do this in the terminal:
```

cat /etc/X11/xorg.conf 

```
and look for the section on it and post here.

---

### Post by kerry_s on 2008-01-20
> **gerfuls said:**
> i have a laptop with a trackpad and a left and right click buttons. how can i middle click (like click down the wheel for autoscroll)???

push the left and right click at the same time.

---

### Post by gerfuls on 2008-01-20
> **erfahren said:**
> what kind of trackpad (or touchpad) is it?

you can look at your /etc/X11/xorg.conf file to see its entry (you can just browse to that file and open it in the text editor - it'll open as read-only)

or you can do this in the terminal:
```

cat /etc/X11/xorg.conf 

```
and look for the section on it and post here.
here is what i saw on the mouse section of the configuration....let me know if you need more! thx

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

---

### Post by erfahren on 2008-01-20
that would be for an external mouse - did you see a section like this?
```

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "MaxTapTime" "0"
	Option	    "SHMConfig" "on"
EndSection

```

---

### Post by mkdotam on 2008-05-24
> **kerry_s said:**
> push the left and right click at the same time.

Thank you!

---

