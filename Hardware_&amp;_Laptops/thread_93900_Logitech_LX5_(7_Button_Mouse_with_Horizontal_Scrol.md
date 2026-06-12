---
title: "Logitech LX5 (7 Button Mouse with Horizontal Scrolling)"
date: 2005-11-23
forum: Hardware &amp; Laptops
---

### Post by audax321 on 2005-11-23
Hello,

      I have Logitech LX5 cordless mouse that I want to get working with Ubuntu. I have the basic three button + vertical scroll wheel functionality, but I want to get the horizontal scrolling working as well. Any idea how I need to edit the xorg.conf file? Do I need to use evdev for this like with the Logitech MX1000?

Thanks. :)

---

### Post by splitsch on 2006-05-20
Hey, I have the same mouse, and I'd like to make it work...I use Dapper...any track I need to follow?

Thanks!

---

### Post by audax321 on 2006-05-29
I got horizontal scrolling working by using evdev. But, I am using Breezy so I'm not sure how Dapper will react. I think the new xorg has some changes made as to how evdev is implemented. But, the mouse section from my xorg.conf is as follows:

```

Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "mouse"
       Option          "SendCoreEvents"
       Option          "Dev Name"              "Logitech USB Receiver"
       Option          "Dev Phys"              "usb-0000:00:1d.0-1/input1"
       Option          "Device"                "/dev/input/mice"
       Option          "Buttons"               "6"
       Option          "Name"                  "Logitech LX5"
       Option          "Protocol"              "evdev"
       Option          "ZAxisMapping"          "4 5 7 6"
EndSection

```

This isn't much different from a standar InputDevice section except that it is using evdev and you need to change the Dev Name and Dev Phys sections for your particular usb port. You get this information by typing the following into a terminal:

```

cat /proc/bus/input/devices

```

You might have multiple entries for Logitech USB Receiver, but I believe you need the one that has mouseX listed as a handler (where X is a number).

Then just edit the Dev Name (probably Logitech USB Receiver) and Dev Phys entries in the xorg.conf section above and hope for the best. Also, the wireless module for the mouse must be plugged into the same USB port everytime for this to work. If you move it, you have to reconfigure the Phys section. And in order for side scrolling to work properly in Firefox, see here:

[http://www.hopstudios.com/nep/unvarnished/item/scrolling_horizontally_with_firefox/](http://www.hopstudios.com/nep/unvarnished/item/scrolling_horizontally_with_firefox/)

Good luck!

---

### Post by bengood24 on 2006-06-25
Just thought I would add that I have achieved success in adding horizontal scrolling with my LX5.

I used the instructions in this thread for the most part:
[http://www.ubuntuforums.org/showthread.php?t=188302](http://www.ubuntuforums.org/showthread.php?t=188302)

I did follow the link above for changing Firefox settings in about:config.
I did not try to use the logitech applet for the higher dpi settings.

In the 19-local.rules I have:
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB RECEIVER", NAME="input/lx5"
```

In the xorg.conf I have:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/lx5"
EndSection
```

And in my .Xmodmap I have:
```
pointer = 1 3 2 4 5 7 6 10 8 9 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32
```

It looks like the first three are for the left right and middle buttons, then the next two are up and down scroll, then the next two are left and right.  Mine was scrolling left and right backwards before I changed 6 7 to 7 6.

This was on 6.06 by the way.

---

### Post by Blender on 2006-07-24
> **bengood24 said:**
> Just thought I would add that I have achieved success in adding horizontal scrolling with my LX5.

I used the instructions in this thread for the most part:
[http://www.ubuntuforums.org/showthread.php?t=188302](http://www.ubuntuforums.org/showthread.php?t=188302)

I did follow the link above for changing Firefox settings in about:config.
I did not try to use the logitech applet for the higher dpi settings.

In the 19-local.rules I have:
```
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB RECEIVER", NAME="input/lx5"
```

In the xorg.conf I have:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "evdev"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/lx5"
EndSection
```

And in my .Xmodmap I have:
```
pointer = 1 3 2 4 5 7 6 10 8 9 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32
```

It looks like the first three are for the left right and middle buttons, then the next two are up and down scroll, then the next two are left and right.  Mine was scrolling left and right backwards before I changed 6 7 to 7 6.

This was on 6.06 by the way.
After following your example and removing all other options in xorg.conf, my side-scrolling finally works. I have been following the guides for the past 30 minutes with no success. Thank you! :)

---

### Post by BdON003 on 2006-10-27
I tried this on 6.10 and could not get it working.  I got errors after the reboot from that guide in the above post.  I am not familiar enough to know what needs to be changed, can anyone else help?

---

### Post by mercuryone on 2007-12-03
I just started to have problems with my LX5. It was working fine for me on Gutsy Xubuntu until this morning (albeit without side-scrolling) when the middle button stopped working altogether. Now the mouse seems to have some strange issues, with Left button being button 1, Scroll Left Button being button 2, Right Button being button 3 and buttons 4 and 5 being Scroll up and down consecutively. There's not any detection at all of the other two buttons (Scroll Right button and Middle button). I tried changing around the xmodmap but to no avail.

Does anybody have any ideas on how to fix this?


Plz help :( any help would be greatly appreciated :KS

---

### Post by Tweenk on 2008-02-16
I have another strange problem with this. On a custom kernel, this mouse's horizontal wheel events are reported as mouse button presses (unfortunately I have removed the build config file). On the generic kernel, they are reported as keyboard events (!) - keycodes XF86Back and XF86Forward. This is VERY weird. This matters because XF86Back and XF86Forward are interpreted as back / forward action in web browsers, while mouse buttons can be configured via Xorg as a horizontal scrolling axis.

EDIT: I think this is the culprit:
```

$ cat /proc/bus/input/devices
...
I: Bus=0003 Vendor=046d Product=c50e Version=2510
N: Name="Logitech USB RECEIVER"
P: Phys=usb-0000:00:1d.2-1/input0
S: Sysfs=/class/input/input2
U: Uniq=
**H: Handlers=kbd mouse1 event2**
B: EV=7
B: KEY=1f0000 0 100 38 c0000000 c0000 0 0 0
B: REL=103
...
```
I have no idea why the kbd driver messes with the mouse. Does anyone know a way to blacklist it for this device?

---

