---
title: "Desktop fades to black, no screen saver"
date: 2008-11-24
forum: General Help
---

### Post by Knoal on 2008-11-24
I'm going to start my own new thread.

I have a fresh install of HH.

I'm using the intergated ATI graphics (3200) on a Asus M3H/HDMI board

The screen fades to black after 60 second of no kbd/mouse activity.

No amount of keybd pounding or mouse moving will bring it back, although the raster (screen crackles with static) will come back on, but no image.

The screensaver is enabled, but never appears (60 seconds).

I have installed the newest ATI cataylist with Envy.

Do I need and xorg update? A new version came out 8/23/08

I'm thnking my xorg needs more info, seems that only the default settings are there, no screen resolution, etc.  I saw it before,then I wiped and retinstalled HH.


xorg.config

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
EndSection

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection



TIA


Knoal

---

### Post by prshah on 2008-11-24
> **Knoal said:**
> 
The screen fades to black after 60 second of no kbd/mouse activity.

No amount of keybd pounding or mouse moving will bring it back,

The screensaver is enabled, but never appears (60 seconds).


I'm thnking my xorg needs more info, seems that only the default settings are there, no screen resolution, etc.

Starting from 8.04, xorg.conf is being marginalized, with a view to phasing it out altogether.

Hence it will contain only basic minimum settings, but it will respect any new settings you manually add (for now, most likely will be dropped altogether in future versions).

Regarding your problem, have you tried changing the screensaver settings to a non-3d screen saver? If that works, then it's most likely a display / OpenGL related issue, otherwise it's likely to be an ACPI / power related issue. 

Post back with the result of changing the screensaver for more troubleshooting.

---

### Post by hollowhead on 2008-11-24
Are you using xsreensaver or gnome, if its gnome replace it with xscreensaver.  I've never managed to get gnomesaver to work it always did this.  If you google replacing gnome with xcreensaver you'll find easy to follow instructions to do this

---

### Post by Knoal on 2008-11-24
Thanks guys!  I'll try the two above suggestions when I get home from work  :)

Hmmmm.... add to list:  remote desktop....


Knoal

---

