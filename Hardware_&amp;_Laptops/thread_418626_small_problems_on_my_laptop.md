---
title: "small problems on my laptop"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by Yvon on 2007-04-22
I have a dell inspiron 9300 laptop. I installed Ubuntu 7.04 on it last know. 
SO far I like it a lot!! 

I have 2 problems though.... 
The touchpad is very sensitive, is there anything to do about that?

Also the wifi internet connection work but it is very slow. It work fine with a cable. 

I'm a linux newbie, so if you need info let me know how to get them! :)

Thanks a lot

---

### Post by hardyn on 2007-04-22
I have had touble with my touch pad as well... i have done two things...
one, find out what touch pad you have (is probably synaptics)

1)intall synapticGTK with synaptic (yes the naming is close)
2)added a touchpad delay after typing (disables touchpad while typing)

installing the synapicGTK is definately the easiest.
the latter requires some editing of the xorg.conf file.

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
EndSection

```

you must add the SHM line.

then add to system->preferences->sessions->startup programs-> "syndaemon -i 1 -d"

---

### Post by Yvon on 2007-04-23
thank you, my touch pad is much better now. 
still have problems with my wireless network though...

---

### Post by hardyn on 2007-04-23
broadcom wireless?  yes you will... there are many many many posts on what works and what doesn't with those things.

good luck.

---

