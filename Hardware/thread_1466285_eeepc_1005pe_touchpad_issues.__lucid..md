---
title: "eeepc 1005pe touchpad issues.  lucid."
date: 2010-04-30
forum: Hardware
---

### Post by tpdean on 2010-04-30
Any Asus eeepc 1005pe users experiencing issues with the touchpad under UNR (Lucid)?  Frequently, I've found that the touchpad doesn't track properly, and gets locked into moving the pointer only in the vertical direction (up/down).  I believe the 1005pe uses a Synaptics touchpad, but may be mistaken...

---

### Post by tpdean on 2010-05-02
The Asus 1005PE does use a Synaptics Touchpad:

# xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)	id=10	[slave  pointer  (2)]
&#9116;   &#8627; [COLOR="Red"]SynPS/2 Synaptics TouchPad [/COLOR]             	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=15	[slave  pointer  (2)]

# cat Xorg.0.log | grep touchpad
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
(**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
(II) Synaptics touchpad driver version 1.2.2
(--) SynPS/2 Synaptics TouchPad: touchpad found
(--) SynPS/2 Synaptics TouchPad: touchpad found

# dmesg | grep Touchpad
[   11.282124] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1a0b1, caps: 0xd04731/0xa40000


No luck figuring anything else out on this...:(

---

