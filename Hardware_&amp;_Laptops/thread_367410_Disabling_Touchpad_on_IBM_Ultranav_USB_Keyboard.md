---
title: "Disabling Touchpad on IBM Ultranav USB Keyboard"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by kyozo on 2007-02-22
Hi,

I have just gotten an IBM USB Ultranav keyboard for my desktop. I love the trackpoint, since I dislike moving the hands away from the keyboard.

However, I have no use for the touchpad, so I would like to disable it. So far all I have been able to find on the net about it, is that you need to have a synaptics device in your xorg.conf for it to work, well I don't have this, and it still works.

This is my input sections in my xorg.conf
```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "dk"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option	   "EmulateWheel" "on"
    Option	   "EmulateWheelButton" "2"
EndSection
```

How du I disable the touchpad without disabling the trackpoint?

I'm running Ubuntu Edgy Eft

When i looked in my DeviceManager i found this entry under USB Controller
```
Ultranav Keyboard Hub
        Ultranav Keyboard
        Composite Touchpad and Trackpoint
                USB HID Interface
                        Synaptics inc. Composite Touchpad / Trackpoint
               USB HID Interface
                        Synaptics inc. Composite Touchpad / Trackpoint

```
So I thought perhaps that it would be possible to just disable the device entirely, but I'm a Linux Noob, so I don't know how to do that.


Thanks in advance

Kyozo

---

### Post by bazmati on 2007-09-11
Anyone helping here ,, this is a direct hit to my issue -- unfortunatly it is not resolved yet!!  please anyone can offer idea on how to disable the touchpad on the ultranav travel keyboard - thanks

---

### Post by bazmati on 2007-09-25
Well after spending a day at this and sanning every possible site about synaptics and touchpad i did something that i'm happy with ,, my touchpad is disabled and my trackpoint works wonderfully -- even got that middle button working as a wheel 

here is what i did   (and thanks to everyone who bothers to post question and replys


first forget about synaptics as the touchpad you want to disable anyway and the trackpoint well it work as an ordinary mouse 

but you have to know which device file the trachpoint uses

To find the trackpoint device file use (as root) cat /proc/bus/input/devices . Look for your device in the list. The device file name will be on the Handlers Line . If there is more than one listed, it is the first one.

then try this basic test, run cat /dev/input/mouse1 (with the appropriate device file) and interact with the touchpad / trackpoint / whatever. if there is no output at all, either the device file is the wrong one, or the kernel driver isn't loaded.

in my case the cat /proc/bus/input/devices  gives

sudo cat /proc/bus/input/devices
Password:

...

I: Bus=0003 Vendor=04b3 Product=3018 Version=0110
N: Name="Lite-On Tech IBM USB Keyboard with UltraNav"
P: Phys=usb-0000:00:1d.1-1.3/input1
S: Sysfs=/class/input/input3
H: Handlers=kbd event3 
B: EV=3
B: KEY=ffff 0 0 28 c000d000 1e0000 0 0 0

I: Bus=0003 Vendor=06cb Product=0009 Version=0100
N: Name="Synaptics Inc. Composite TouchPad / TrackPoint"
P: Phys=usb-0000:00:1d.1-1.4/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse2 ts1 event4    <==== this is what you are looking for
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

now sudo 
cat /dev/input/mouse1  or ts1   or try mouse1 (that was my touchpad)  and move all of your mouses untill you find witch device file is the trackpoint  if you get garbage chr when you move mouse ,, the test is positive

Another good place to check for debug is the Xorg.0.log

my mouse section now looks like that 
(**) Configured Mouse: Device: "/dev/input/mouse2"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mouse2"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Option "EmulateWheel" "true"
(**) Option "EmulateWheelButton" "2"
(==) Configured Mouse: YAxisMapping: buttons 4 and 5
(**) Configured Mouse: EmulateWheel, EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(**) Configured Mouse: Buttons: 9

now regarding the xorg.conf file this is what it should look like
remember # means commented out

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
#        InputDevice    "Synaptics Touchpad" "CorePointer'
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "ca"
	Option	    "XkbVariant" "multix"
EndSection

 Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mouse2"   
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
	Option	"EmulateWheel" "true"
	Option 	"EmulateWheelButton" "2"
 EndSection

#Section "InputDevice"
#	Identifier "Synaptics Touchpad"
#	Driver 	"synaptics"
#	Option 	"SendCoreEvents" 
#	Option 	"Device" "/dev/input/mouse1"
#	Option 	"Protocol" "auto-dev"
#	Option 	"HorizScrollDelta" "1"
#	Option 	"SHMConfig" "on"
#	Option 	"VertTwoFingerScroll" "true"
#	Option 	"HorizTwoFingerScroll" "true"
#	Option 	"TapButton1" "0"
#	Option 	"TapButton2" "3"
#	Option 	"TapButton3" "2"
#EndSection

Then when i rebooted my system (after the 50th time)  i was super happy to notice that the trackpoint was now disabled PERIOD...   forget the SHMConfig = true to then use qsynaptics to disable the touchpod,,, simply force the system to use the trackpoint,,, and that worked for me.  HOPE you get to enjpy -now-  the BEST KEYBOARD EVER  

let me know if that worked for you ,,

---

### Post by kyozo on 2007-12-30
Hi,

First off sorry about the long delay - but I have been terrible busy, and haven't used my home PC very much.

But now in the holidays, I have a little off time, so I can mess with this a little.

I followed your advice, and it works as a charm.

Apparently, in my Xorg.conf I was just having an entry that said /dev/input/mice, after using your simple test to cat the device files i found out that my touchpad had dev/input/mouse1 and my trackpoint had /dev/input/mouse2, so I simply replaced the line /dev/input/mice with /dev/input/mouse2. restarted X (pressing ctrl-alt-backspace), and voila it worked.

By the way, I've upgraded to Ubuntu 7.10 in the meanwhile.

Cheers

Kyozo

---

### Post by GeneralCody on 2008-03-04
Else it is an option to just disable the trackpad in the BIOS...
At least on my Thinkpad...

:)

---

### Post by kyozo on 2008-03-04
> **GeneralCody said:**
> Else it is an option to just disable the trackpad in the BIOS...
At least on my Thinkpad...

:)

Yes, I know you can do that on a ThinkPad, but mine is a separate USB Keyboard for a desktop PC, so I can't do that :)

I might use your advice when I install Ubuntu on the Thinkpad provided by my employer :) Although that might not be in the nearest future :(

/Kyozo

---

