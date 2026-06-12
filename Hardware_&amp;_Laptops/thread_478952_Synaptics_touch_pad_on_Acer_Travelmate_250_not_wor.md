---
title: "Synaptics touch pad on Acer Travelmate 250 not working"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by repo74 on 2007-06-19
Hi there guys and gals,
 I have a problem with my Synaptics touchpad. I have tried Gsynaptics, Qsynaptics, and I looked in xorg.conf and there is no mention of a Synaptic touchpad at all. I have also looked in device manager and there is a mention of there being one but every time I try to run  Gsynaptics I get this

 GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

I have entered this manually as read from a post here 

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"		"true"
EndSection

but no go.

Now I have read and read all things on this forum about how to enable it but nothing works. I even tried what someone suggested in another thread about downgrading to an older version, but nothing has altered. At one point I managed to kill the gui but got it working again after copying the backup I had of xorg.conf lol.  I tried typing synclient -h but got this below

Can't access shared memory area. SHMConfig disabled? So now what do I do I am a lowly newbie so any help appreciated. 

:(

---

### Post by repo74 on 2007-06-20
*bump*

Please guys give me a bit of help, I really want to solve this problem.

Thanks

---

### Post by repo74 on 2007-06-20
Never mind, I solved the problem myself. Just had to make a few commands in gedit tpof. ;)

---

### Post by mikeypizano on 2007-06-20
Hey, I am also having problems like you, can you tell me how you fixed it?

---

### Post by repo74 on 2007-06-22
Hi there, just follow the instructions on this page to the letter and it will work 

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Cheers :)

---

