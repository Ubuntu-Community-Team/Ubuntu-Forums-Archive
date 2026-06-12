---
title: "synaptics touchpad driver"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by stevieb on 2006-07-14
hello,
does anyone know how i can check whether the synaptics touchpad driver is installed on my system, and change my xorg.conf to reflect its presence?  also, what is the name of the driver?

thanks,
-steve

---

### Post by encompass on 2006-07-14
try tap to click... or middle click with two fingers and right click with three fingers... Thats how I know it is working.:-D

---

### Post by stevieb on 2006-07-14
tap to click works- that's the problem.  i want to turn it off, but there's no entry for synaptics in xorg.conf.

---

### Post by philippe_carlo on 2006-07-14
[This link]("http://www.justlinux.com/forum/showthread.php?t=144294") is for XFree but I think it should work for you too.

---

### Post by philippe_carlo on 2006-07-14
This thread is also interesting: [http://www.ubuntuforums.org/showthread.php?t=160209]("http://www.ubuntuforums.org/showthread.php?t=160209")

---

### Post by didobuntu on 2006-07-14
I recently succeeded to make turn on/off the synaptic touchpad

I don't remember which thread I followed in this forum, but thanks for all the solidarity of these guys ...

I had to add two things in the xorg.conf file : 

1. I added the following section:

Section "InputDevice"
        Identifier      "touchpad"
        Driver          "synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
        Option "ShmConfig" "true"
EndSection


2. And I added the line  ... InputDevice "touchpad" "AlwaysCore" ... in the ServerLayout section. Now its looks like this:

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        InputDevice     "touchpad" "AlwaysCore"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

---

### Post by stevieb on 2006-07-14
I've tried those suggestions, but qsynaptics is asking me to "please install the synaptics touchpad driver!"

Can someone point me to this, and instructions on how to correctly install it?
thanks,
-steve

---

