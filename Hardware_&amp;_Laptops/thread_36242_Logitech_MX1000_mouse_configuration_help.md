---
title: "Logitech MX1000 mouse configuration help"
date: 2005-05-22
forum: Hardware &amp; Laptops
---

### Post by Fandu on 2005-05-22
I'm new to linux, and am trying to get my logitech mx1000 working with hoary.  I found [this page](http://blog.blackdown.de/2005/04/03/logitech-mx1000-configuration/) that describes how to set it up.  However, I don't understand how to get the evdev driver going.  Any help would be much appreciated.  Thanks

---

### Post by Sam on 2005-05-22
[QUOTE=Fandu]I'm new to linux, and am trying to get my logitech mx1000 working with hoary.  I found [this page](http://blog.blackdown.de/2005/04/03/logitech-mx1000-configuration/) that describes how to set it up.  However, I don't understand how to get the evdev driver going.  Any help would be much appreciated.  Thanks[/QUOTE]
Try this [howto](http://www.ubuntulinux.org/wiki/ManyButtonsMouseHowto/).

---

### Post by Fandu on 2005-05-22
I had already found several guides on the forums for getting 5 button mice working, However the mx1000 is a 12 button mouse, and the only guide I've found to getting it going is the one I linked above.  Is my understanding correct that to get the other 7 buttons working, you have to install the evdev driver?

---

### Post by jkreileder on 2005-05-22
[QUOTE=Fandu]I'm new to linux, and am trying to get my logitech mx1000 working with hoary.  I found [this page](http://blog.blackdown.de/2005/04/03/logitech-mx1000-configuration/) that describes how to set it up.  However, I don't understand how to get the evdev driver going.  Any help would be much appreciated.  Thanks[/QUOTE]
There are two evdev drivers:

[list=1]
[*]Kernel evdev:
This module should get loaded by hotplug. When the module is loaded you should see /dev/input/event* devices.
(The kernel option for this is CONFIG_INPUT_EVDEV.)

[*]X evdev:
Gets loaded by 'Option "Protocol"  "evdev"' in the X server configuration.
The value for 'Option "DevName"' must be same as in /proc/bus/input/devices.
[/list] 

As long as Ubuntu kernels include the evdev module and the module isn't blacklisted in /etc/hotplug* the HOWTO should work fine.

---

### Post by jkreileder on 2005-05-22
[QUOTE=Fandu]I had already found several guides on the forums for getting 5 button mice working, However the mx1000 is a 12 button mouse, and the only guide I've found to getting it going is the one I linked above.  Is my understanding correct that to get the other 7 buttons working, you have to install the evdev driver?[/QUOTE]
It should be installed already, you just have to enable its use.
'evdev' is a more generic input driver than the 'mouse' driver, it's the only way to get  all buttons working on MX1000 currently.

---

### Post by Fandu on 2005-05-23
OK, I still can't get this to work and it's really bugging me.  I checked /etc/hotplug/blacklist and evdev is not listed there.  Here is my /proc/bus/input/devices:
```
I: Bus=0003 Vendor=046d Product=c50e Version=2500
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.2-2.7/input0
H: Handlers=kbd mouse0 event2 ts0 
B: EV=120007 
B: KEY=ffff0000 10000 0 0 0 0 0 0 0 
B: REL=103 
B: LED=fc00 
``` 

And this is the relevant /etc/X11/xorg.conf part:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
        Option          "ZAxisMapping"          "6 7"
        Option          "Resolution"            "100"
EndSection
```

And here's what I'm replacing it with:

```
Section "InputDevice"
        Identifier  "Configured Mouse"  #I had to use this ident, else x complains
        Driver         "mouse"
        Option        "Protocol"           "evdev"
        Option        "Dev Name"        "Logitech USB Receiver" 
        Option        "Dev Phys"          "usb-0000:00:02.2-2.7/input0"
        Option        "Device"              "/dev/input/mice" 
        Option        "Buttons"            "12"
        Option        "ZAxisMapping"   "11 12"
        Option        "Resolution"        "800"
EndSection
```

X will start with this config, but the buttons are all mapped wrong?!?!

here's the /etc/X11/Xmodmap I'm using:
```
! Configured Mouse
pointer = 1 2 3 8 9 10 11 12 6 7 4 5
```

and this is ~/.xbindkeysrc:
```
# Backward and Forward buttons
"xvkbd -text "\[Alt_L]\[Left]""
  m:0x10 + b:8
"xvkbd -text "\[Alt_L]\[Right]""
  m:0x10 + b:9
	
# "Cruise Control" disabled:
#"xvkbd -text "\[Page_Up]""
#  m:0x10 + b:11
#"xvkbd -text "\[Page_Down]""
#  m:0x10 + b:12
	
# "Cruise Control" enabled:
# Only use this if you have problems with Mozilla
#"NoCommand"
#  m:0x10 + b:11
#"NoCommand"
#  m:0x10 + b:12
	
# Application-Switch button
# A-Tab doesn't work
# Use it as another Forward for now
"xvkbd -text "\[Alt_L]\[Right]""
  m:0x10 + b:10

```

I installed xbindkeys and xvkbd from apt-get and I'm starting xbindkeys in the gnome startup programs.  Any idea what I'm doing wrong??

---

### Post by jkreileder on 2005-05-24
You need ZAxisMapping "11 12 10 9" to get the tilt wheel working and you probably should remove the "/dev/input/mice" line.

As for xmodmap, I've written the HOWTO for Debian which read /etc/X11/Xmodmap when logging in via gdm. I'm not sure if Ubuntu does that too (check /etc/X11/Xsession.d/). You can load the file manually with 'xmodmap /etc/X11/Xmodmap'.

---

