---
title: "Stylus calibration on wacom tablets"
date: 2008-05-23
forum: Hardware
---

### Post by roy.nico on 2008-05-23
Hej, 

I have a laptop Fujitsu T4220, with a Wacom tablet. By default, the stylus is not perfectly calibrated, this means, the cursor does not appear exactly under the stylus. For this, the solution i found is :
* using ```
xidump stylus
``` i try to get the right values for TopX, TopY, BottomX and BottomY.
* Then, i set them with ```
xsetwacom set stylus TopX value
xsetwacom set stylus BottomX value
xsetwacom set stylus TopY value
xsetwacom set stylus BottomY value
```

This works, but to avoid doing this at each reboot, i can fix the values in the xorg.conf file, e.g. :

```
	Option		"BottomX"	"18350"
	Option		"TopX"	"130"
	Option		"BottomY"	"24450"
	Option		"TopY"	"0"

```

The problem, is that if then i rotate the screen, the same values wil be used, and the position of the cursor will be **completely ** wrong !

So, my question : is there a way to save two sets of values, 1 for landscape mode and 1 for portrait mode ? I guess it is impossible in xorg.conf. But maybe in some rotation-script (that i don't know where they are) ?

Thanks in advance for any comment.

Nicolas

---

### Post by roy.nico on 2008-05-31
up?

Nicolas

---

### Post by highcc on 2008-09-14
Hi Nicolas,

I don't know if you still waiting for the solution of your problem, but since I got in this thread from google, I think it would be useful posting here.
I have a HP tx2110us (wich have a wacom "penabled" screen too) and got my stylus working right now and was looking for a way to calibrate it.

This site [http://mirosol.kapsi.fi/tx2020/tx2000howto.htm](http://mirosol.kapsi.fi/tx2020/tx2000howto.htm) has a topic on rotating screen, I hope it helps you and others.

Vitor

---

### Post by gali98 on 2008-09-15
A tutorial for usb wacom tablet pc's that I wrote is here....
It covers this issue...
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)

enjoy :)
Kory

---

