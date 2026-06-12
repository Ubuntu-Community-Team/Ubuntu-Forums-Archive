---
title: "Trackpad (driver?) missing on Lenovo E555 running 14.04"
date: 2015-11-11
forum: Hardware
---

### Post by Timothy Taylor on 2015-11-11
I am trying to get the TrackPad on my Lenovo E555 to work.

The TrackPad works in basic "mouse" mode, but gestures, scrolling, etc are not recognised. 
No Touch Pad settings tab appears in System/Preferences/Mouse

The TrackPad is there though:
> **sudo tpconfig -i]
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled said:**
> 

but 
[QUOTE=sudo synclient]Couldn't find synaptics properties. No synaptics driver loaded?

Lenovo tech support are utterly useless, saying that Linux is not supported, even though the E555 is on the "approved hardware" list for pre-installed systems.
There must be a full set of Linux drivers for the E555 somewhere...?

I also found [Synaptics Gesture Suite Linux for TouchPads]("http://www.synaptics.com/en/gesture-suite-linux.php"), but there's no indication of where I can download it.
:(

---

