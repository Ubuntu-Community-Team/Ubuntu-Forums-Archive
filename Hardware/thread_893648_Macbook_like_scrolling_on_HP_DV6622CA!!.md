---
title: "Macbook like scrolling on HP DV6622CA!!"
date: 2008-08-18
forum: Hardware
---

### Post by shak541 on 2008-08-18
wow i can;t belive this works... you guys know how macbooks can scroll with 2 fingers? i can do it on my hp laptop without any actualy hardware tweaking!!! its amazing!! if anyone wants info please post here. Just to tell you guys.... it a little bit glitchy but almost perfect once you get used to it!! :D

---

### Post by pwnprog on 2008-08-18
seriously??? how did you get that working, or did it do it right out of the box? i have an hp dv6660se , which i am assuming is a similar box.

---

### Post by shak541 on 2008-08-18
haahhahaha!! i knew someone would be interested... hold your 2 fingers so one is right above the other one when using the scrolling..

so liek this
.
.

make sure that they are as straight as possible... also this is a bit glitchy so it may take some getting used to.
here is what you have to change in /etc/X11/xorg.conf
:
Section "InputDevice" 
        Identifier "Synaptics Touchpad"
        Driver "synaptics"
	 Option		"SendCoreEvents"	"true"
        Option "Device" "/dev/input/touchpad"
        Option "Protocol" "auto-dev"
        Option "VertScrollDelta" "20"
        Option "HorizScrollDelta" "350"
        Option "VertTwoFingerScroll" "true"
        Option "HorizTwoFingerScroll" "true"
        Option "FastTaps" "false"
        Option "TapButton2" "3"
        Option "AccelFactor" "0.3"
        Option "SHMConfig"  "on"
EndSection

replace that whole section and it will work after restarting x or rebooting your laptop! :D
enjoy! :D

EDIT: umm can you please tell me if this worked for you? and if so ... how well? thanks
EDIT2: also hold your fingers right against each other. or the pad will just make the mouse jump. this feature is really picky because the touchpad in macbooks has multitouch.. whereas the hp ones do not :(
EDIT3:try not to move your fingers too much. it should only need minimal movement. as in shift the weight of your fingers.

---

### Post by pwnprog on 2008-08-18
haha. alright i think i might give this a shot. but first, by "glitchy" do you mean that this could make my entire system glitchy? this is my main os and i must use it for schoolwork, so i don't wanna throw anything off balance yknow?

---

### Post by shak541 on 2008-08-18
no nothing else is changed at all.. only the part in for xorg.conf file is modifyed... just make a backup of that part of the file and your set. nothing else is changed at all.. enjoy!!! :D

---

### Post by shak541 on 2008-08-19
bump.... has anyone else here tested this out?
EDIT: your fingers can be in any way.. as long as they are vertical or horizontal. just make sure your fingers move at the same time and speed and this neat little trick works.

---

