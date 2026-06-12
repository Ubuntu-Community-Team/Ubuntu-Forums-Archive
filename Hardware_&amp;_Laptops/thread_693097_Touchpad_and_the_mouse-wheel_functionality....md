---
title: "Touchpad and the mouse-wheel functionality..."
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by neocortex on 2008-02-10
There are many posts regarding how-to make touchpad more functional. I have easily disabled tapping, which is very irritating -- too sensitive and making lots of mess. In proper place in '/etc/X11/xorg.conf' file, I just added: <Option		"SHMConfig"		"on">
[CODE]
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"on"
[\CODE]
Then, I added a line under System > Preferences > Sessions > Startup Programs:
[CODE]
synclient TapButton1=0 TapButton2=0 TapButton3=0 RTCornerButton=0 RBCornerButton=0
[\CODE]
(There were some problems to make this part running, but if you think, it is related to privileges -- you need to be a root or so. I admit, I forgot how I managed to make this working.)

Now, my question: I really like that mouse-wheel-click, where you can select some piece of text, for example, and paste it just by click with the mouse-wheel. How can I do this with the Touchpad? My life would be much easier if that would be possible. So, please, anyone to help...

Best,
PM

---

