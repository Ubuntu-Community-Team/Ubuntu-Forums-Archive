---
title: "Laptop wont start X without usb mouse plugged in"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by mattmcmanus on 2007-04-15
Hello All,

I've got a problem that i've been trying to track down for two weeks now and I'm at my wits end with it. I've got a Velocity Micro L80, which is a Compal HEL80. It has an Elantech Touchpad. 

My problem is that X wont start unless I have my usb mouse installed. X complains that there is now syntaptic touchpad. I can plug the mouse in while x starts and remove it immediately and the touchpad will work find with no problems at all. 

Here is the bit from the log:

```
(II) Synaptics touchpad driver version 0.14.6 (1406)
Synaptics Touchpad no synaptics event device found (checked 19 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "SHMConfig" "on"
(**) Option "HorizScrollDelta" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
```

I have my xorg.conf file as follows for the mice

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "evdev"
    Option         "Name" "Logitech USB Gaming Mouse"
    Option         "ZAxisMapping" "4 5 6 7"
    Option         "Emulate3Buttons" "false"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "Device" 	"/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "SHMConfig" "on"
    Option         "HorizScrollDelta" "0"
EndSection
```

Now, I am pretty new to linux so i've been trying to figure out how things work. [this post]("http://ubuntuforums.org/showthread.php?t=219894") helped a bit regarding this issue. I ran

```
cat /proc/bus/input/devices
```

To see where the touchpad was mounted but from what came up there appeared to be nothing related to my touchpad. 

```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 event0 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.0-1/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f

I: Bus=0003 Vendor=046d Product=c517 Version=0110
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.0-1/input1
S: Sysfs=/class/input/input3
H: Handlers=kbd mouse1 event3 ts1 
B: EV=f
B: KEY=7fff 2c3027 bf004440 0 0 ff0001 f80 8807c000 667bfa d941dfed 9e0000 0 0 0
B: REL=143
B: ABS=1 0

I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio4/input0
S: Sysfs=/class/input/input4
H: Handlers=mouse2 event4 ts2 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=ACPI_FPB/button/input0
S: Sysfs=/class/input/input5
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/class/input/input6
H: Handlers=event6 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input7
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0

```

Is there something im missing? I hope this is enough information. Any information you can give would be a lot of help. Thanks so much. 

Oh, im running the most recent version of Feisty.

---

### Post by cokhavim on 2007-04-16
i had a similar problem with my logitech v200 cordless mouse.  i fixed the problem by changing the options in my xorg.conf:

```
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"             #specific option for my touchpad
        #Option         "VertScrollDelta"       "0"            #specifc option for my touchpad (not enabled)
        Option          "MaxTapTime"            "0"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        #Option         "CorePointer"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/input/event9" #this should be that underlined name from 19-local.rules
        Option          "HWHEELRelativeAxisButtons"     "7 6"    #this is a specific option for my mouse
EndSection

```

i found that the option "SendCoreEvents" "true" was the important factor in solving this problem (for both the touchpad and the mouse).  and i also had to comment out the option "CorePointer".

i hope that helps!

---

### Post by mattmcmanus on 2007-04-16
Wow, I can't believe it was that simple. In a different situation I would be embarrassed but I am so happy to have this working! 

Thank you so much

---

### Post by cokhavim on 2007-04-17
yeah, it took me a while to figure it out too! :)

---

