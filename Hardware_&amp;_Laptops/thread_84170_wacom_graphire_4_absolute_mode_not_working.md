---
title: "wacom graphire 4: absolute mode not working"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by nojjy on 2005-10-30
I recently installed a wacom graphire4 tablet and absolute mode does not seem to be working:  it behaves in relative mode whether or not xorg.conf is configured correctly.  Here is the configuration information I have:

```
Section "InputDevice"
        Identifier "cursor"
        Driver 		"wacom"
        Option 		"Device" "/dev/input/event1"
	Option		"Mode"		"absolute"   
        Option 		"Type" "cursor"
        Option		"USB" "on"
EndSection

Section "InputDevice"
        Identifier "stylus"
        Driver "wacom"
        Option "Device" "/dev/input/event1"
        Option "Type" "stylus"
	Option		"Mode"		"absolute"   
        Option "USB" "on"
EndSection

Section "InputDevice"
        Identifier "eraser"
        Driver "wacom"
        Option "Device" "/dev/input/event1"
        Option "Type" "eraser"
        Option "USB" "on"
EndSection
```

```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
        InputDevice     "cursor"     "AlwaysCore"
        InputDevice     "stylus"     "AlwaysCore"
        InputDevice     "eraser"     "AlwaysCore"
EndSection

```

Am I missing anything?  Help is appreciated.

---

### Post by 23meg on 2005-10-30
Try entering the following at the terminal:

```
xsetwacom set cursor mode absolute
xsetwacom set eraser mode absolute
xsetwacom set stylus mode absolute
```

If there are errors, ignore them if the mode is correctly set.

---

### Post by nojjy on 2005-10-30
23meg, tried your suggestion and unfortunately it did not set the tablet to absolute mode.  I recieved the following error:

Error (5): WacomConfigSetRawParam: Unknown X error
Set: Failed to set (cursor,erasor,stylus) value for 'Mode'

I may be wasting my energy on this problem, as graphire4 tablets aren't officially supported yet.  Still, they don't appear too different from graphire3 tablets.

---

### Post by 23meg on 2005-10-30
Hmm, not sure about the state of support on Graphire4, but you could ask on the linuxwacom mailing list. There are some very knowledgeable people there and  they may have hacks to help you even if your tablet isn't officially supported yet.

---

### Post by nojjy on 2005-10-30
OK I solved the problem... simple solution: I was pointing to the wrong 'event' device, event1.  It should have been 'event2'.  All works well now.  Thanks for the help, though I feel a bit foolish.

---

