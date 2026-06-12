---
title: "Synaptic touchpad recognized as Wacom tablet"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by sloco on 2007-02-04
I recently installed Dapper Drake AMD64 on my Gateway 7422GX laptop.  I am a noob so please be gentle.  The Synaptic touchpad is behaving badly under Ubuntu and Mandriva so far.  While rolling over a button or feature it may change focus, select it, click it, or do nothing.  This causes rapid unintended switching between open windows, randomly typing into the wrong application.  The tap to click, tap-drag, and scroll features do not work at all.
I installed QSynaptics but it says that no driver is installed.  I need instructions.  Device manager shows it as SynPS/2 Synaptics TouchPad, /org/freedesktop/Hal/devices/platform_i8042_i8042_Aux_Port_logicaldev_input
But /etc/X11/xorg.conf contains this:

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

There are no Wacom devices present on this machine as far as I know.
slo

---

### Post by sloco on 2007-02-04
Well, I followed instructions I found elsewhere on this forum and added sysnaptics entries to /etc/X11/xorg.conf this allowed qsynaptics to recognize that the synaptics driver was installed and shared memory was on.  However changing settings in Qsynaptics has no effect on anything.  Things are now worse and even less predictable.  Cursor movement is now very slow.  Some clicks now register that didn't before, hyperlinks for example. A tap within a text box results in pasting from the clipboard, clicking a firefox tab closes it. the verticle scroll works but any leftward movement gets the same result as repeatedly clicking backspace, I still cant click on ok boxes, min, max or some other common buttons.  Regular clicks with the physical buttons do not register untill after they are released.  Really strange behavior.

---

### Post by bsell on 2007-02-13
Try using gsynaptics instead of qsynaptics. Worked for me, I don't know if it will work for you, though.

---

### Post by kolesarm on 2007-02-23
> **sloco said:**
> There are no Wacom devices present on this machine as far as I know.
slo

The same thing happened to me after reinstallation of dapper - it misrecognised the touchpad as a wacom device. Solution that worked to me:
[ubuntu help]("https://help.ubuntu.com/community/SynapticsTouchpad").

---

