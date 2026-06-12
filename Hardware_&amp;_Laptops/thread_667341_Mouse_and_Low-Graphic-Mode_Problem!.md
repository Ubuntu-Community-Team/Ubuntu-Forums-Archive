---
title: "Mouse and Low-Graphic-Mode Problem!?"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by ephemeralDream on 2008-01-14
Greetings, I have a Toshiba laptop running ubuntu 7.10 with Microsoft Comfort Mouse 3000.

My problem is whenever I plug-out my mouse before ubuntu boot up, ubuntu will be put into low graphic mode. But if I plug in the mouse and reboot, everything back to normal.

Below is the mouse portion of the XORG.CONF. I only modified this input device part for mouse and remove the original one (Driver "mouse", Protocol "IS/PS2" , etc).

```

Section "InputDevice"
       Identifier     "Configured Mouse"
       Driver         "evdev"
       Option	      "CorePointer"
       Option         "Name" "Microsoft Microsoft Optical Mouse with Tilt Wheel"
       Option         "DIALRelativeAxisButtons" "7 6"
EndSection

```

Is there any work around for it? Thank you very much for your kind assistance. I am deeply appreciated.

Regards,

---

### Post by tgalati4 on 2008-01-15
You can have multiple input devices.  Leave both entries.  Also compare the results of:

>lsmod

between boots with and without the mouse.  Perhaps there is a module that gets loaded.  If that is the case, then put that module in /etc/modules so it is always loaded.

---

### Post by ephemeralDream on 2008-01-15
Thank you very much, tgalati4!!! You really save me (a linux noob) lot of troubles. It works like charm now. I added "evdev" line into "/etc/modules" and it works faultlessly.

Regarding the multiple input devices, I have to put my configuration for my mouse first before the original entry. Else it won't work, as in all my mouse button messed up, even xmodmap pointer won't help.

Thank you once again.

EDIT: if I add an entry in "Session" to xmodmap my mouse, and while the mouse is not plug-in at boot, ubuntu will enter low graphic mode again. I try to add line in modules again, but I have no idea which is the module for xmodmap pointers. I hope you can enlighten me again.

---

### Post by ephemeralDream on 2008-01-15
Hi, today, it is not working again!!!  =((  

When plug out the mouse and reboot, Xorg.0.log is below:

== Original XORG.conf == (WORK)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(--) Synaptics Touchpad touchpad found
(II) NVIDIA(0): Setting mode "1024x768"
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
SetClientVersion: 0 9


== When putting my conf portion for Comfort Mouse == (NOT WORK ! =( )
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(--) Synaptics Touchpad touchpad found
Synaptics DeviceOff called
Synaptics DeviceOff called

Regards,

---

