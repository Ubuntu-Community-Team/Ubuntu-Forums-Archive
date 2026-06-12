---
title: "Here we go again...radeon 9000"
date: 2008-11-28
forum: General Help
---

### Post by larryfroot on 2008-11-28
Hi everyone...

Once upon a time in hardyland my ati radeon 9000 (in a dell latitude D600 laptop) would do the compiz thing surprisingly well with the following hack to xorg.conf and a SKIP_CHECKS=yes compiz with the open source drivers

aSection "Device"
Identifier "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
Driver "ati"
BusID "PCI:1:0:0"
Option "XAANoOffscreenPixmaps"
Option "DisableGLXRootClipping" "true"
Option "AddARGBGLXVisuals" "true"
Option "AllowGLXWithComposite" "true"
Option "EnablePageFlip" "true"
Option "GARTSize" "64"
Option "MergedFB" "off"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Virtual 1920 1440
Modes "1400x1050"
EndSubSection
EndSection

Section "ServerLayout"
Option "AIGLX" "true"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection

Now it is all bad, not a glimmer of a compiz anywhere. 

glxinfo tells me that the gl is mesa, which is not so good, if memory serves. If anyone can tell me how to progress from here, that would be dandy. Oh, I'm currently running with the open source drivers - tried the fglrx but no good. At least the open source doesnt chew up and spit out the modded xorg.conf given.

Thanks to anyone who can help...seems a shame to leave compiz behind with Hardy...

---

### Post by overdrank on 2008-11-28
If you are using Hardy then you may try the xfix option when booting in to recovery mode.

---

### Post by larryfroot on 2008-11-28
Thank you for your reply, but I am afraid I was unclear, my apologies. It  used to work fine with hardy, its trying to get the radeon 9000 to work with compiz/intrepid thats the problem.

---

### Post by inigomontoya on 2008-11-29
Post the output of glxinfo.  Try commenting out the GartSize option and add: ```
Option "BusType" "PCI"
```

Sounds crazy but it worked for me to get direct rendering enabled.

---

