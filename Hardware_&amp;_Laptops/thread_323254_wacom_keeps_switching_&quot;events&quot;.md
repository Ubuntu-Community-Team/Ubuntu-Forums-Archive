---
title: "wacom keeps switching &quot;events&quot;"
date: 2006-12-21
forum: Hardware &amp; Laptops
---

### Post by corstar on 2006-12-21
this problem has me scratching my head...
I have a fully working wacom tablet that works great with Gimp, Krita and Inkscape. All the kernel sources are working fine.

But, every time I reboot or switch the system off, the wacom "event" switches over to another number.

At first, I had it plugged it into a 4 port usb hub, so then plugged it into the back of the motherboard usb.

That didn't fix the problem. It's REALLY annoying typing "sudo cat /dev/input 0-5"
 and editing the X org.

Is there a solution out there?

here's the input of xorg.

> Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/event5"   # USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/event5"   # USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/event5"   # USB ONLY
  Option        "Type"          "cursor"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

---

### Post by xscd on 2006-12-23
USB and other hot-pluggable devices often "switch events" or change the names by which they are (temporarily, while they are plugged in) referred to, to accommodate other devices which may have already been plugged in before them during the same session, for example. To address that problem, some very helpful people created the wacom-tools package, that you can install using synaptic. The wacom-tools package is a set of udev scripts and rules that make your USB Wacom tablet always be named:

/dev/input/wacom

The way that this is accomplished is that the wacom-tools scripts look for the actual event that your USB Wacom tablet **happens to be at the time**, and instantly makes a symbolic link (nickname) for that event in the /dev/input directory called "wacom"

This is very useful, because after you install the wacom-tools package (and reboot the computer), instead of editing your xorg.conf file all the time and typing the correct "event"--

Option "Device" "/dev/input/event1"
or
Option "Device" "/dev/input/event2"
or
Option "Device" "/dev/input/event3"
(or whatever the correct device happens to be at the time)

--you only need to edit your xorg.conf file once, and change all of those particular lines that pertain to the Wacom stylus, eraser and cursor, to:

Option "Device" "/dev/input/wacom"

:)

Please be aware that Xorg looks at its configuration file **only** when it starts up. So **after** you install the wacom-tools package, and after you edit the xorg.conf file and reboot the computer or restart the Xorg server, **remember this**:

If you plug in your USB Wacom tablet **after** you are already logged into the GUI (Gnome or KDE or Fluxbox or whatever GUI you use), or if you are already at the GDM login screen (or KDM or...), you will need to **restart the Xorg server** so that it will reread its configuration file, see the Wacom tablet, and begin to use the Xorg Wacom driver (wacom_drv.o) to read the tablet's data from the tablet's "device file" in the /dev/input directory. The easiest way to restart the Xorg server is to log out (temporarily) and then, when you are back to the graphical login screen, press this key combination: CONTROL-ALT-BACKSPACE.

(Beware, this is **not** control-alt-delete, but control-alt-backspace.)
:)

For (much) more information about the Wacom tablets, use Ubuntuforums "Search" feature and enter the word "wacom" (without the quotes).

Enjoy your tablet. I use a Wacom USB Intuos3 6x11 widescreen tablet in my Ubuntu Edgy Eft installation. It works great in the GUI (I use Gnome) and in the Gimp as well as the great vector graphic program Inkscape.

Good luck and best wishes,

---

