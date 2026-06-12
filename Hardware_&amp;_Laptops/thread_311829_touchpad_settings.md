---
title: "touchpad settings"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by woopud on 2006-12-03
Is there a way to disable touchpad tapping ?  It's really sensitive so things open up al the time unwanted.

Bert

---

### Post by giruzz on 2006-12-05
Same problem here...

did you solve anything?

giruzz

---

### Post by roger99 on 2006-12-05
try installing gsynaptics, you'll find through synaptic or apt-get.  You'll get a touchpad menu option under System -> Preferences.

It worked for me.

---

### Post by Patrick-Ruff on 2006-12-05
open the xorg conf, and then find the area where the snaptics touchpad exists . . . 

then enter the following

Option                 MaxTapTime             "0"

that should kill tapping. however, the snaptics utility which I wasn't aware of, seems like a much better solution.

---

### Post by OttifantSir on 2006-12-07
I installed gsynaptics and I get an error message saying I have to set SHMConfig to true in either xorg.conf or XF86Config.

I can't find this entry in xorg.conf, and I don't have XF86Config (as far as I have seen. locate is the command for finding files, right?)

So, if I need to add this to xorg.conf, where do I add it?

---

### Post by eggdeng on 2006-12-07
I don't think you need any of that stuff. Open a terminal & type

sudo synclient TouchpadOff=1

to disable and

sudo synclient TouchpadOff=0

to enable. If you want a quick script to start up with the touchpad disabled by default, let me know.

---

### Post by giruzz on 2006-12-07
Hi,

What I've done is:

sudo kwrite /etc/X11/xorg.conf   

Under the section:
> Section "InputDevice"
	Identifier	"Synaptics Touchpad"

Just add this:

	> Option		"TouchpadOff"		"1"

Hope it helps

g.

---

