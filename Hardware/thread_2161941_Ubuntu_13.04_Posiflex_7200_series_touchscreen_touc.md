---
title: "Ubuntu 13.04 Posiflex 7200 series touchscreen touch registering as hover?"
date: 2013-07-12
forum: Hardware
---

### Post by mlabieniec on 2013-07-12
I have a new posiflex 7200 series with a USB touch screen. The device shows up fine and evtest even runs fine and interacts with touches. The only issue is the actual funcionality of touching something other than when using evtest does not work. If I touch an icon..etc. I get almost a "Mouse Over" functionality (I get a tooltip show up in the launcher bar), and when I release my finger, I get a beep. So I know the touch is registered, but seems to not be functioning correctly. If I run xinput_calibrator I get the screen but can not touch the areas on the screen (on release I do get the beep, but screen does not register the touch and move on). I checked the contents of /usr/share/X11/xorg.conf.d/ and have:


10-evdev.conf
11-evdev-quirks.conf
11-evdev-trackpoint.conf
50-synaptics.conf
50-vmmouse.conf
50-wacom.conf
51-synaptics-quirks.conf


And sudo evtest displays:


    /dev/input/event2:	Posiflex Inc. USB TOUCH V390


So I know it's there but am stumped on getting the touch functioning correctly. Also, in /dev/input/by-id:


    lrwxrwxrwx 1 root root   9 Jul 12 09:41 usb-Posiflex_Inc._USB_TOUCH_V390-event-mouse -> ../event2
    lrwxrwxrwx 1 root root   6 Jul 12 09:41 usb-Posiflex_Inc._USB_TOUCH_V390-mouse -> ../js0

---

### Post by mlabieniec on 2013-07-16
[COLOR=#444444][FONT=UbuntuRegular]Found one similar issue online: [comments.gmane.org/gmane.linux.kernel.input/30758]("http://comments.gmane.org/gmane.linux.kernel.input/30758") still no resolution though, I've contacted tech support supposably they have linux drivers for the screen.[/FONT][/COLOR][COLOR=#444444][FONT=UbuntuRegular] [/FONT][/COLOR]

---

