---
title: "Alps TouchPad on an Compal / Zepto 2415w!!!"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by urbanus on 2006-11-02
I've sort of got the Alps Touchpad working.

Here's my situation:
1. I make an error in the "xorg.conf" file so that X doesn't start. (Maybe someone out there know's how to just shut X down. I don't)
2. Then fix it, enters X from command line ("startx").
3. Then i log out to command line and enter X again. Now my Touchpad works and I'm is able to configure it from "gsynaptics". 
But this isn't very practical.

To test wether it works (I don't mean wether u can use it or not....you know what I mean), use this command: "synclient -m 1"
If it gives output when u touch the touchpad, the driver works as it should.
On my pc it doesn't give output when I logon as normal. Only when I do as described above.

CAN ANYONE EXPLAIN THIS FOR ME????? PLEASE!!!!

Heres the relevant code from my "xorg.conf" file:
> 
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 
	InputDevice    "Generic Keyboard"
	#InputDevice    "Configured Mouse"
	InputDevice 	"touchpad" "AlwaysCore"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "synaptics"
EndSection

Section "InputDevice"
        Identifier      "TouchPad"
	Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection


I use the xorg synaptics driver and "gsynaptics" to configure the touchpad.

I have an:
> I: Bus=0011 Vendor=0002 Product=0008 Version=7321
N: Name="AlpsPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input6
H: Handlers=mouse1 event5 ts1 
B: EV=f
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: REL=3
B: ABS=1000003

Use "cat /proc/bus/input/devices" to get this output.

I have as stated in the headline a Zepto 2415w pc, it's a Compal pc. Not shure witch model.

PS! If I use the event to identify my touchpad, then the number of the event will change when I restart to something different, 
then the one I had before I restarted and choose to use in my xorg.conf file.



If anyone can solve this "problem", then many people will have working thouchpads :)

---

