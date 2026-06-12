---
title: "Multiple Mouses"
date: 2005-08-11
forum: Hardware &amp; Laptops
---

### Post by zappa86 on 2005-08-11
I have two mouses. (Dont ask me way) But I can only use one in ubuntu. One is PS2 amd the other is USB and I would like to use both. I'm nure sure how to do it.

---

### Post by One Quick Question on 2005-08-11
I have that too.
It's actually very easy to do, just edit your /etc/X11/xorg.conf file.

You'll need to duplicate the InputDevice section for the mouse, and change the name and what which device it is, depending exactly on what kind of mice they are. Er, that is, they can both be /dev/input/mice, but for me, that causes one of the mice to go nuts.   Also, since one is a USB, check out this often-quoted page: [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=46](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=46)
It may not be completely relevant to you, but it's got lots of information.

And then under the ServerLayout section, put in the new mouse name.

This is what parts of my xorg.conf file looks like:

```

Section "InputDevice"
  Identifier "MX 1000"
 Driver  "mouse"
 Option  "SendCoreEvents"
 Option  "Protocol" "evdev"
 Option  "Dev Phys" "usb-0000:00:1d.3-*/input0" 
 Option  "Device" "/dev/input/mice"
 Option  "Buttons" "12"
 Option  "ZAxisMapping" "11 12"
 Option  "Resolution" "800"
EndSection


Section "InputDevice"
 Identifier "Old Mouse"
  Driver  "mouse"
  Option  "SendCoreEvents"
 Option  "CorePointer"
 Option  "Device"  "/dev/input/mouse0"
  Option  "Protocol"  "ImPS/2"
  Option  "ZAxisMapping"  "4 5"
EndSection

```and then```

Section "ServerLayout"
 Identifier "Default Layout"
 Screen  "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "MX 1000"
  InputDevice "Old Mouse"
EndSection

```
Something or other like that should work.
And if not, hopefully it will point you in the right direction!

---

