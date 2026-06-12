---
title: "Mouse pointer freeze"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by Talar on 2007-08-08
The problem is that my mouse pointer will freeze after using the desktop for some time, it could be after 15 minutes or 3 hours, but eventually it will lock up. Everything else seems to be running normally, I can keep using my applications through the keyboard and open console windows, but if I try to restart the X server when this happens it will just hang and a hard reboot is necessary.

I have a GeForce 7950 and I'm running a fresh install of Kubuntu 7.04, but the problem is probably not Kubuntu-related since I have experienced it when running Ubuntu, Mandriva and Slackware livecds as well and I have tried both Gnome and KDE.

I have tried using different driver packages both nv and nvidia in Kubuntu but had similar problems with both.

I thing I have noticed is that I always seem to get a lockup when I try to change any configuration related to the graphics drivers, for example replacing them in Adept. To do this I need to boot without the gui.

I'm not sure exactly what could cause this problem and would appreciate any ideas.


This is the xorg.log 22.41 is just around when a freeze happened:

Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
AUDIT: Tue Aug  7 22:41:47 2007: 4976 X: client 31 rejected from local host (uid 0)
AUDIT: Tue Aug  7 22:41:47 2007: 4976 X: client 31 rejected from local host (uid 0)
AUDIT: Tue Aug  7 22:41:47 2007: 4976 X: client 31 rejected from local host (uid 0)
AUDIT: Tue Aug  7 22:43:16 2007: 4976 X: client 31 rejected from local host (uid 0)


Parts of current xorg.conf:

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "se"
  option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ImPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/input/wacom"
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/input/wacom"
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/input/wacom"
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
  identifier "Generic Video Card"
  boardname "nv"
  busid "PCI:1:0:0"
  driver "nvidia"
  screen 0
EndSection

---

