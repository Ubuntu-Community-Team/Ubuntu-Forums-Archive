---
title: "t400s multitouch..."
date: 2009-11-20
forum: Hardware
---

### Post by gooood on 2009-11-20
Hi!
I'm seriously considering buying a Thinkpad t400s as a fulltime linux machine.
The only doubt I have is regarding its multitouch trackpad. I searched on that forum and it is not really clear to me what can be done...
The only thing that I really want is the two finger scrolling. 3 fingers gestures would be great too but I can live without them :P

Thanks,
Francesco

---

### Post by tgalati4 on 2009-11-20
Two-finger scrolling works on a T43p so I see no reason why it wouldn't work on newer thinkpads.  You can also set 3-finger functions, various tap functions, vertical and horizontal edge scrolling.

There are a lot of specialized thinkpad utilities:

tgalati4@tpad-Gloria7 ~ $ apt-cache search thinkpad
acpitool - command line ACPI client
acpitool-dbg - command line ACPI client (debug)
gkrellm-thinkbat - ThinkPad laptops battery status indicator for GKrellM
hdaps-utils - HDAPS (IBM Hard Drive Active Protection System) utilities
kopete-plugin-thinklight - thinkpad flashing for kopete
pidgin-blinklight - Blinks your ThinkPad's ThinkLight upon new messgaes
tleds - blinks keyboard LEDs for TX and RX network packets
tp-smapi-source - Source for the tp_smapi kernel modules
tpb - program to use the IBM ThinkPad(tm) special keys
mwavem - Mwave/ACP modem support software
tpfand - Controls fan speed of ThinkPad notebooks
hdapsd - HDAPS daemon for IBM/Lenovo ThinkPads and Apple iBooks/PowerBooks

There are also settings available in your /etc/X11/xorg.conf file:

#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizScrollDelta"	"0"
#	Option		"VertTwoFingerScroll"	"1"
#	Option		"HorizTwoFingerScroll"	"1"
#EndSection
# for trackpoint buttons to activate center scroll button
#Option 		"EmulateWheel" "true"
#Option 		"EmulateWheelButton" "2"

You can also install gsynaptics for even more control.

---

### Post by gooood on 2009-11-21
Thanks for the information!
I was just scared by this page: [http://www.thinkwiki.org/wiki/Install_Ubuntu_9.10_(Karmic_Koala)_on_a_ThinkPad_T400s]("http://www.thinkwiki.org/wiki/Install_Ubuntu_9.10_(Karmic_Koala)_on_a_ThinkPad_T400s") and this topic: [http://ubuntuforums.org/showthread.php?t=1264148&highlight=t400s]("http://ubuntuforums.org/showthread.php?t=1264148&highlight=t400s")

---

