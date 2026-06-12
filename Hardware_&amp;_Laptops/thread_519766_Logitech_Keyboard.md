---
title: "Logitech Keyboard"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by DWRZ on 2007-08-07
I know Logitech sucks when it comes to Linux support/drivers, so I was wondering if anyone knew if and to what extent their [Cordless Desktop MX5000 Laser (Mouse and Keyboard)]("http://www.logitech.com/index.cfm/keyboards/keyboard_mice_combos/devices/162&cl=us,en") worked on Ubuntu. Otherwise, any place I can go to check hardware/accessories compatibility with Linux? 

Many thanks,
DWRZ

---

### Post by liquid circuit on 2007-08-07
I'm using the Logitech MX5000 / MX1000 Bluetooth combo on Ubuntu 7.04 (Feisty) with most of the extra buttons working.

If I remember correctly, I was able to get the mouse/keyboard working pretty easily doing the basics.  The keyboard/mouse combo can connect to the included dongle without using Bluetooth (using basic RF, just like a basic wireless keyboard/mouse).  I'm pretty sure this worked correctly as soon as I connected and booted into Ubuntu.  However, in the basic RF mode, none of the extra buttons work.  What you need to do is get the device connected using Bluetooth... I used the following articles to get everything working as I wanted.  I probably found other stuff on the net that may have helped/hindered.  Since I just started using Linux at about the same time I got the keyboard/mouse combo, I was learning a lot while trying to get this all working as I needed, so my memory is a bit hazy as to what I was doing right/wrong.  The point is though, as a total Linux noob, I was able to get everything working correctly eventually.

[Get the Logitech MX5000 / MX1000 working through Bluetooth in Ubuntu]("http://ubuntuforums.org/showthread.php?t=432013")

[Get all the buttons working on the Logitech MX1000 Bluetooth mouse]("https://help.ubuntu.com/community/MX1000Mouse")

[Get most of the extra keys working on the Logitech MX5000 Bluetooth keyboard]("https://help.ubuntu.com/community/KeyTouch")

One problem I have run into is that the mouse won't connect on bootup unless I'm constantly moving it.  If that happens, X won't start as there is no core pointer.  In that case, I just jump into the terminal and run *sudo hidd --search* with a press of the button on the mouse to get it re-connected, and then *sudo /etc/init.d/gdm restart* to restart X.

In the end, you can get it working; I've got the multimedia keys on the keyboard controling Amarok, and controlling my overall amixer volume (for my M-Audio Audiophile 2496) using scripts.  I've got the mouse working for back/forward in Firefox and Nautilus, the tilt-wheel is configured to switch tabs in Firefox (which I find much more useful than horizantal scrolling), and the task-switcher button is set up to initiate the Scale plugin in Beryl when combined with Alt (I couldn't find a way to do this with a single button press on the mouse).  I'm very happy with the setup, and the re-connection issue with the mouse on boot isn't really that a big deal now that I have setup scripts/aliases to make the commands easier to remember if needed.

---

### Post by liquid circuit on 2007-08-07
Oh!  I just remembered something that I had trouble figuring out.  [The guide I linked to]("https://help.ubuntu.com/community/MX1000Mouse") that describes how to get the extra buttons working on the MX1000 wasn't intended for the Bluetooth version of this mouse, but it still works.  The only major difference, if I recall correctly, was in the following section:

> First, let's make a backup of your xorg.conf and then open it up for editing. In a terminal:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
```

#

Find the section that looks like:

```
Section "InputDevice"
       Identifier       "Configured Mouse"
...
EndSection
```

#

Go ahead and delete this section (don't worry we made the backup in case anything goes wrong) and replace it with the following:

```
Section "InputDevice"
        Identifier      "Logitech MX1000"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Receiver"
        Option          "HWHEELRelativeAxisButtons" "7 6"
EndSection
```

The "Name" is case sensitive and should be exactly the same as the one shown by

```
cat /proc/bus/input/devices
```

What we need to do, since we are using bluetooth, is replace the line...
```
Option          "Name"          "Logitech USB Receiver"
```
with what is reported by *cat /proc/bus/input/devices*...
```
Option          "Name"          "Logitech Bluetooth Mouse"
```

I mention this because I had originally screwed up and used the line...
```
Option          "Name"          "Logitech Logitech BT Mini-Receiver"
``` as this was also reported (with the double "Logitech Logitech") by *cat /proc/bus/input/devices* and seemed to match with the guide... however this didn't work (which made sense once I actually thought about it).

---

### Post by Dougie085 on 2007-08-23
I can't get this to work for anything. I can get them to connect in the same session but i restart and nothing.

---

