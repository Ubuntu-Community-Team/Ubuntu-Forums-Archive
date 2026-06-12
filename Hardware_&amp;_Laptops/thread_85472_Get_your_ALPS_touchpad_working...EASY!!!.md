---
title: "Get your ALPS touchpad working...EASY!!!"
date: 2005-11-02
forum: Hardware &amp; Laptops
---

### Post by jjoyner on 2005-11-02
Here are the stipulations:
1 - MAKE A COPY OF YOUR XORG.CONF (past this into your gnome-terminal session:> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup.
2 - Touchpad has to be working currently (as in moving and clicking)
3 - If you plug in a USB mouse after doing this, it will kill the settings.  You will have to unplug the mouse and "Init 1" or Ctrl+Alt+Bkspc...moreover you prolly should reboot to be safe.
4 - You need to install Synaptics drivers: > sudo apt-get install xorg-synaptics-driver or do this through the Synaptic Package Manager (no relation).

Now on to the good stuff...
Go to terminal and type -
> # sudo cat /proc/bus/input/devices

You will see a device with the identifier "Configured Mouse"...leave it alone.  You will additionally see something like "ALPS Glidepoint Touchpad" (or something different) as an identifier.  Go down to handlers and it should look something like this:

> handlers: ts1 event1 mouse1 (mine was 2)

Now mark down what "event" your touchpad was.  Now:

Now go to > /etc/input and look for that "event"...to make sure it is there....(it will prolly be black and yellow textwise).

> #sudo gedit /etc/X11/xorg.conf

Go down to Section "InputDevice"...make sure you go past "Configured Mouse" again...you will notice the identifier again (i.e "ALPS Glidepoint Touchpad"(or something different)). 

In the 'Option   "Device"' line, you should see something like "/dev/input" or "psaux" or "/dev/input/mice".  Replace this with "/dev/input/event*#*" (*#* being your event number).

If you want vscrolling, tapping, hscrolling, etc, you need to add these lines in the same area following the same pattern:
> Section "InputDevice"
Identifier "ALPS"
Option "LeftEdge" "120"
Option "RightEdge" "830"
Option "TopEdge" "120"
Option "BottomEdge" "650"
Option "VertScrollDelta" "10"
Option "HorizScrollDelta" "0"
Option "MinSpeed" "0.45"
Option "MaxSpeed" "0.75"
Option "AccelFactor" "0.020"
Option "EdgeMotionMinSpeed" "200"
Option "EdgeMotionMaxSpeed" "200"
Option "UpDownScrolling" "1"
Option "CircularScrolling" "0"
Option "SHMConfig" "true"


OR you can download [qsynaptics]("http://qsynaptics.sourceforge.net/") and have a cutsie little interface to work with.

[http://qsynaptics.sourceforge.net/](http://qsynaptics.sourceforge.net/)

Or at least this is how I got my r3000z touchpad working in 5.10 Breezy....:D

---

