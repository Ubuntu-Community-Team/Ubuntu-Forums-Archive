---
title: "Logitech v450 in Edgy"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by kylevan on 2006-12-27
Ok, after some struggling with udev rules and other such silliness (not that udev is silly, but for my application it's not necessary,) I've finally gotten my lovely new Logitech v450 totally working - the tilt wheel even tilts in the right directions :rolleyes: 

For this tutorial, I'm going to assume that you're using a laptop like I am.  I've read pretty much every guide I could in doing this, and all the complicated stuff wasn't happening, but a combination of the following was mint.

[http://ubuntuforums.org/showpost.php?p=1155987&postcount=62](http://ubuntuforums.org/showpost.php?p=1155987&postcount=62)
[http://ubuntuforums.org/showpost.php?p=1435903&postcount=4](http://ubuntuforums.org/showpost.php?p=1435903&postcount=4)

What you need to do is get the "Phys" string for the device out of the /proc files.  Make sure your receiver is plugged in and the mouse turned on.

```
cat /proc/bus/input/devices
```

You'll get two entries with the name "Logitech USB Receiver".  One I believe is there to handle keyboard events, the other is the mouse.  Switching the two caused problems like no tomorrow.  What you want is the one with the "phys" string ending in "input0"

```
I: Bus=0003 Vendor=046d Product=c518 Version=4203
N: Name="Logitech USB Receiver"
**P: Phys=usb-0000:00:1d.7-2.5/input0**
S: Sysfs=/class/input/input5
H: Handlers=mouse1 event3 ts1 
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
```

This will uniquely identify the correct device, even if you unplug and plug back in.  You then need to modify your xorg.conf file (back it up first!) somewhat like the [first article I linked to]("http://ubuntuforums.org/showpost.php?p=1155987&postcount=62").  One important change is that we are going to swap the "CorePointer" designation to the built-in touchpad.  It may not be necessary, but at least if everything somehow goes wrong, you'll have a working X server with the touchpad.

The two "InputDevice" sections should look something like the following, just make sure to replace the "Dev Phys" option with the correct string you found when you did the "cat /proc/bus/input/devices".  Remember to completely delete the "Configured Mouse" configuration.

```
Section "InputDevice"
        Identifier      "Logitech v450"
        Driver          "evdev"
        Option          "Name"                          "Logitech USB Receiver"
        Option          "Dev Phys"                      "usb-0000:00:1d.7-2.5/input0"
        Option          "HWHEELRelativeAxisButtons"     "7 6"
        Option          "SendCoreEvents"                "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        ***Option          "CorePointer"***
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "true"
EndSection

```

Your touchpad may not be a Synaptics, but the main point is to show that there is no "SendCoreEvents" option defined, and instead we give the touchpad the CorePointer option which I highlighted.  Basically it becomes the "main mouse," and since the touchpad is always attached to the laptop, you shouldn't get an X crash because of no mouse.  If for some reason you are using this mouse on a desktop with no other mice, you'll want to place the CorePointer in with the logitech mouse section, making sure you delete the SendCoreEvents line as well.

Finally, you need to head to the "ServerLayout" section of your xorg.conf file and look for the "Configured Mouse" line, and change it to "Logitech v450".  Now, say your hail marys, and hit CTRL+ALT+Backspace to restart X - make sure you understand how to restore the backed up xorg.conf before you do.

Hopefully everything has worked properly for you.  From here, you can check out [detyabozhye's HUGE howto]("http://ubuntuforums.org/showthread.php?t=219894") on setting up keybindings for things like back/forward in nautilus, etc.  The default functionality for the tilt wheel should be back/forward in FireFox, and left/right scrolling in pretty much everything else I've used.

Thanks to everyone who has grappled with working around Logitech's lack of Linux Drivers and utilities, and documented their experience.
[http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)
[http://aarongyes.com/guides/mx1000](http://aarongyes.com/guides/mx1000)
[https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse)
[https://help.ubuntu.com/community/G7Mouse](https://help.ubuntu.com/community/G7Mouse)
...a bunch of other documentation that I've forgotten to list.

---

### Post by superfool on 2007-01-17
Thanks for the guide. It helps, I was having some problem at first since I still had my  **SendCoreEvents** in the **Synaptics Touchpad** section, but once I removed it, things are working great.
Another difference so that people can tell if it's a mouse receiver or keyboard receiver is to check the Handlers, it should contain a word **"mouse[x]"**, the other receiver has the word **"kbd"** instead (which is keyboard I think) .

```

I: Bus=0003 Vendor=046d Product=c518 Version=4203
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.7-2.5/input0
S: Sysfs=/class/input/input5
**H: Handlers=mouse1 event3 ts1 **
B: EV=7
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
```

**EDIT**: I deleted the udev rule and things went wrong, so in order to make this work and even we don't use the event, we still have to define the udev rules, you can refer to [THIS GUIDE]("http://ubuntuforums.org/showthread.php?t=219894") to do it.

---

### Post by kylevan on 2007-01-21
strange, I don't even have an additional rules file. :confused:   well, as long as it worked for you!

---

### Post by ajmatson on 2007-02-04
My v450 works on startup but when I open firefox tabs it stops responding and I have to restart my computer to get it to work again. I tried the xorg.conf trick but it was not in there so I added the v450 section and restarted X but it crashed. Any ideas??

---

### Post by arsya on 2007-03-05
Finally, I could make use all the V450 buttons. That's really great.
I just follow what you mention in your guide. I don't even need to add udev rule.
Thanks for the great tutorial.

regards,
Arsya

---

### Post by golem3 on 2007-04-15
Thanks, BigV. I will give it a try today or later.
 
You're a great help. :D

---

### Post by Miguel on 2007-05-13
Hi guys,

Just bought a V450 a couple of days ago, but I'm thinking on returning it. The thing is that I feel it's a bit too sensitive, or that the sensor feels a bit anisotropic (i.e., more sensitive in horizontal than in vertical). Any similar issues? What's your config in Gnome (or KDE)?

---

### Post by golem3 on 2007-05-30
> **Miguel said:**
> Hi guys,

Just bought a V450 a couple of days ago, but I'm thinking on returning it. The thing is that I feel it's a bit too sensitive, or that the sensor feels a bit anisotropic (i.e., more sensitive in horizontal than in vertical). Any similar issues? What's your config in Gnome (or KDE)?

KyleVan (BigV)'s posting really improves the v450 in Feisty. It allows the rocker on the middle button (scroll) to work. 

I find that the v450 is a great mouse.

---

### Post by Grump60 on 2007-07-29
Thank you for the  excellent tutorial.  I had to make the Identifier in xorg.conf "Configured Mouse" otherwise the X server would not start, everything else exactly as you indicated.  This was with Feisty on a Dell Inspiron 5150.

---

### Post by olavjunior on 2008-05-13
Old thread, sorry. But I can't get this to work in Hardy! Any changes to how Hardy handles mice?

---

### Post by gitpik on 2008-06-26
I am also having trouble with this in Hardy. Every change to xorg.conf I try only gives me a dead mouse. Anyone have any ideas?

---

### Post by amd-64 on 2008-07-03
I am using Ibex Intrepid and here is my xorg.conf

```

Section    "InputDevice"
Identifier "Logitech v450"
Driver     "mouse"
Option     "Name"              "Logitech USB Receiver"
Option     "Dev Phys"          "usb-0000:00:1d.2-1/input0"
Option     "HWHEELRelativeAxisButtons"   "7 6"
Option     "SendCoreEvents"    "true"
Option     "Device"            "/dev/input/mice" # <-- add this line 
EndSection

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver     "synaptics"
Option     "CorePointer"
Option     "Device"        "/dev/psaux"
Option     "Protocol"      "auto-dev"
Option     "HorizScrollDelta" "0"
Option     "SHMConfig"     "true"
EndSection

```

Note that I needed a device line in the Logitech section to get this to work.

---

### Post by gitpik on 2008-07-08
Thanks amd-64! that missing line and btnx got that worked out for me :)

---

