---
title: "help assigning laptop hotkeys"
date: 2008-09-27
forum: Hardware
---

### Post by mexus on 2008-09-27
I have **ASUS F3KE-AP056**
I need to get all the fast keys working. Now only some of them are working.
XEV don't recognize all of them but KeyTouch editor does.
Running: Kubuntu 8.04

Here is a list of all the keys:
KEY  /   What does (should do)  / **KeyTouch event**
[COLOR="DarkGreen"]
FN+F1 - sleep - works (nothing to be done) **button/sleep SLPB 00000080**[/COLOR]
    
[COLOR="Sienna"]FN+F2 - Toggle wireless/bt off (doesn't work) **hotkey ATKD 0000005d**[/COLOR]

[COLOR="Indigo"]FN+F3 - Open mail (works*) **hotkey ATKD 00000050**

FN+F4 - Launch WWW browser (works*) **hotkey ATKD 00000050**
The same as WWW button next to power button[/COLOR]

[COLOR="DarkSlateGray"]FN+F5 - brightness down (works**) **video LCDD 00000087 00000000**

FN+F6 - brightness up (works**)** video LCDD 00000086 00000000**[/COLOR]
[COLOR="DarkGreen"]
FN+F7 - turn on/off LCD illumination (works) **hotkey ATKD 00000034**[/COLOR]

[COLOR="Sienna"]FN+F8 - Switch display config Panel/Panel+VGA/Panel+DVI/Panel+SVHS
/VGA/DVI/SVHS (doesn't work) **hotkey ATKD 00000064**

FN+F9 - Disable/Enable Touchpad (doesn't work) **hotkey ATKD 0000006b**
The same as Touchpad button next to power button[/COLOR]

[COLOR="Indigo"]FN+F10 - Mute (works*) - **hotkey ATKD 00000032**

FN+F11 - Volume down (works*) - **hotkey ATKD 00000031**

FN+F12 - Volume up (works*) - **hotkey ATKD 00000030[/COLOR]**
[COLOR="Sienna"]
FN+Space - Power profiles (doesn't work - should change kpowersave profiles) **hotkey ATKD 0000005c**
The same as Powergear button next to power button

FN+C - Display Color profiles (doesn't work) **hotkey ATKD 0000008a**
The same as Splendid button next to power button

FN+V - Start Webcam (doesn't work) **hotkey ATKD 00000082**[/COLOR]
[COLOR="Indigo"]
FN + UP - Stop (works*) **hotkey ATKD 00000043**

FN + Down - Play/pause (works*) **hotkey ATKD 00000045**

FN + Left - Prev track (works*)** hotkey ATKD 00000040**

FN + Right - Next track (works*) **hotkey ATKD 00000041**

FN + T - Phone (works*) **hotkey ATKD 00000099**
[/COLOR]
[COLOR="Blue"]Master WIFI/BT Switch OFF (works***) **hotkey ATKD 00000081**
Master WIFI/BT Switch ON (works***) **hotkey ATKD 00000080**
[/COLOR]
[COLOR="Indigo"]* - works if configured with keytouch[/COLOR]
[COLOR="DarkSlateGray"]** - works if kpowersave is running[/COLOR]
[COLOR="Blue"]*** - works fine, but led indication is not correct (BT led is always on, and wifi is always off)[/COLOR]

Can someone help me with the non working buttons.

I'll provide as much info i can find about my laptop so it will be fully supported by Ubuntu/kubuntu.

---

### Post by binbash on 2008-09-27
I am using a similar laptop.asus f3sr

FN+V - Start Webcam (doesn't work) hotkey ATKD 00000082 
arrange cheese command to that button.


FN+F9 - Disable/Enable Touchpad (doesn't work) hotkey ATKD 0000006b
The same as Touchpad button next to power button

I saw a script 2 days ago at tutorials section which enables and disables touchpad.You can get the script and arrange that commant to that key.(Yes you have to find the topic first :) )


FN+F2 - Toggle wireless/bt off (doesn't work) hotkey ATKD 0000005d

You have to write a custom bash script for this.I do not know how to disable wireless but you can disable bluetooth via /etc/init.d/bluetooth stop.But this will be a little complicated since the script should check the wireless and bluetooth status.A couple "If" will do the trick.

---

### Post by mexus on 2008-09-27
OK like here are some scripts from /etc/acpi

touchpad

event:
```
# /etc/acpi/events/asus-touchpad
# This is called when the user presses the touchpad button and calls
# /etc/acpi/asus-touchpad.sh for further processing.

event=hotkey ATKD 0000006a
action=/etc/acpi/asus-touchpad.sh
```

sh
```
#!/bin/sh

# get the current state of the touchpad
TPSTATUS=`synclient -l | grep TouchpadOff | awk '{print $3}'`

# if getting the status failed, exit
test -z $TPSTATUS && exit 1

if [ $TPSTATUS = 0 ]; then
   synclient TouchpadOff=1
else
   synclient TouchpadOff=0
fi

```
```

And this doesn't work. The keycode is the same as mine

```
Here are scripts for wireless (they don't work too)

wireless 1 (the FN +2)
event
```
#!/bin/sh

# get the current state of the touchpad
TPSTATUS=`synclient -l | grep TouchpadOff | awk '{print $3}'`

# if getting the status failed, exit
test -z $TPSTATUS && exit 1

if [ $TPSTATUS = 0 ]; then
   synclient TouchpadOff=1
else
   synclient TouchpadOff=0
fi

```

sh

```
#!/bin/sh
# Find and toggle wireless devices on Asus laptops

. /usr/share/acpi-support/state-funcs

toggleAllWirelessStates;

# Update the Asus LED to reflect the new status of the wireless
! isAnyWirelessPoweredOn;
setLEDAsusWireless $?

```

wireless 2
event
```
# /etc/acpi/events/asus-wireless
# This is called when the user presses the wireless button and calls
# /etc/acpi/wireless.sh for further processing.

event=hotkey ATKD 0000005[ef]
action=/etc/acpi/asus-wireless-2.sh %e

```

sh
```
#!/bin/sh

. /usr/share/acpi-support/state-funcs

ON_VALUE="e"
OFF_VALUE="f"

CHARACTER_POSITION="8"

HOTKEY_VALUE=`echo "$3"| cut -b "$CHARACTER_POSITION"`

if ( isAnyWirelessPoweredOn && [ "$HOTKEY_VALUE" =  "$OFF_VALUE" ] ) || ( ! isAnyWirelessPoweredOn && [ "$HOTKEY_VALUE" =  "$ON_VALUE" ] ) ; then
	toggleAllWirelessStates
fi
```

---

