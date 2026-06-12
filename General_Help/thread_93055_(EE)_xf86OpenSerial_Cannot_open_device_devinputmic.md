---
title: "(EE) xf86OpenSerial: Cannot open device /dev/input/mice"
date: 2005-11-21
forum: General Help
---

### Post by fishacre on 2005-11-21
Hi,

I'm newish to Linux, and completely new to these forums - apologies if I'm posting this in the wrong place...

I installed Breezy on my laptop (Acer Aspire 1360) a couple of weeks ago (from a CD made a couple of weeks before that), & until  yesterday it was working perfectly. The last thing I did was install R (version 2.2), & all of a sudden on rebooting the X server fails to start...

The errors I get are:

(EE) xf86OpenSerial: Cannot open device /dev/input/mice
          No such file or directory.
(EE) Configured Mouse: cannot open input device
(EE) PreInit failed for input device "Configured Mouse"
(II) UnloadModule: "mouse"
(II) Synaptics touchpad driver version 0.13.6
Synaptics Touchpad no synaptics event device found (checked 1 nodes)
(**) Option "Device" "/dev/psaux"
(EE) xf86OpenSerial: Cannot open device /dev/psaux
         No such file or directory.
Synaptics driver unable to open device
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule "synaptics"
(WW) No core pointer registered
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
No core pointer

Fatal server error:
failed to initialize core devices



Maybe I should say I only use the touchpad, not a mouse. I don't see what I could have done to screw this up - not only is there no /dev/input/mice, there is no /dev/input.....

Any suggestions very welcome!

f.

---

