---
title: "How to calibrate touchscreen on a Lifebook B2610?"
date: 2007-12-18
forum: Hardware &amp; Laptops
---

### Post by lifeisbetterwithketchup on 2007-12-18
I have a Fujitsu Lifebook B2610 (P3 800Mhz, 256MB RAM).  It has a touchscreen.  The touchscreen responds, however; it is way off calibration.  How would I go about calibrating the touchscreen?  I am running Ubuntu Gutsy.

Thanks.

---

### Post by lifeisbetterwithketchup on 2007-12-24
bump?

---

### Post by edrex on 2008-01-06
hi lifeisbetterwithketchup, i have the same lifebook, still wheezing along. good product. The instructions below should work not only with lifebook touchscreens, but various other touchscreens supported by the evdev kernel module.

I'm running Gutsy now, where thankfully the evtouch driver ([http://www.conan.de/lifebook/lifebook.html](http://www.conan.de/lifebook/lifebook.html)) is now installed by default IIRC. The calibration program is also included at */usr/lib/xf86-input-evtouch* and it works! Whoever maintains this package has done some great integration work recently b/c it used to be horribly broken (feisty maybe?) and before that you had to install manually (the binaries on conan's site work fine with older ubuntu versions).

The required udev rule, on the other hand, is not included with Gutsy. Without this file, your touchscreen may randomly alternate between different device names each time you reboot (mine does). 

**Basic Setup**

Copy the file 69-touchscreen.rules from the [latest evtouch source archive]("http://www.conan.de/touchscreen/xf86-input-evtouch-0.8.7.tar.bz2") to the directory /etc/udev/rules.d/. Not sure you have to reload udev, but to be safe:
```
sudo udevcontrol reload_rules
```

Add a section to your /etc/X11/xorg.conf like so:
```
Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event1"
    Option "DeviceName" "touchscreen"
    Option "MinX" "98"
    Option "MinY" "43"
    Option "MaxX" "940"
    Option "MaxY" "925"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
EndSection
```

Also add this line to your ServerLayout section:
```
InputDevice "touchscreen" "CorePointer"
```
Your touchscreen should now basically work. For non-lifebook screens, axis flipping may be required, not sure.

**Calibrating**

Switch to VT1 (ctrl-alt-F1), run ```
sudo /etc/init.d/gdm stop
```, and edit xorg.conf (hint: vi) adding the line 
```
Option "Calibrate" "1"
```
to the touchscreen section. Be sure not to miss the quotes or anything. "On" doesn't work, I tried :)

```
cd /usr/lib/xf86-input-evtouch/
sudo ./calibrate.sh
```

Instructions for using the calibrate prog are in /usr/share/doc/xserver-xorg-input-evtouch/README.calibrate. It's very finicky and unintuitive. Also check out /usr/share/doc/xserver-xorg-input-evtouch/README.Debian

My config up ended looking like:
```
Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/evtouch_event"
    Option "DeviceName" "touchscreen"
        Option        "MinX"        "76"
        Option        "MinY"        "104"
        Option        "MaxX"        "957"
        Option        "MaxY"        "976"
        Option        "x0"        "0"
        Option        "y0"        "3"
        Option        "x1"        "7"
        Option        "y1"        "2"
        Option        "x2"        "1"
        Option        "y2"        "1"
        Option        "x3"        "-3"
        Option        "y3"        "0"
        Option        "x4"        "10"
        Option        "y4"        "-2"
        Option        "x5"        "9"
        Option        "y5"        "0"
        Option        "x6"        "0"
        Option        "y6"        "2"
        Option        "x7"        "10"
        Option        "y7"        "3"
        Option        "x8"        "5"
        Option        "y8"        "0"
	Option "ReportingMode" "Raw"
#	Option "Calibrate" "1"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
EndSection
```

I had to run the calibrate process several times, and then manually adjust the values for each control point. Even though in the calibrate prog you start in the top-left and scan down, the points are actually layed out like this:
6 7 8
3 4 5
0 1 2
And the deltas are in screen coordinates (larger X values move the cursor to the right, larger Y moves down). For fine-tuning I just left vi open on the VT and continually restarted X with ctrl-alt-backspace until it was just right. Good luck!

**Tweaking Event Timing/Buttons**

There are a number of additional options which modify the behavior of your touchscreen. The basic timing and event options are listed [here]("http://www.conan.de/touchscreen/evtouch.html#config"). Additionally, in the most recent versions it is possible to flexibly map touchscreen events to mousebutton events as documented on the [libtouch]("http://www.conan.de/touchscreen/libtouch.html") page.

I think it would be very cool to whip up some profiles of the above settings for different applications (graphics, gaming...)

**Ideas for improving the driver**
I understand that the synaptics xorg input driver has an Option SHMConfig which allows on-the-fly configuration (ie without restarting X). Not sure if this is a generic X option that might work for the evtouch driver as well, but I think it would be great to have a gui touchpad calibration and profile manager to allow dynamic switching between profiles. See [this issue]("https://bugs.launchpad.net/ubuntu/+source/ksynaptics/+bug/3406") regarding ksynaptics

PS If anyone comes up with more touchscreen tips, please share.

---

### Post by edrex on 2008-01-06
[This guy]("http://lists.freedesktop.org/archives/xorg/2007-October/029740.html") talks about calibration using the joystick driver for his elotouch touchscreen. Interesting, and probably would work with the lifebook touch device too :)

---

### Post by lifeisbetterwithketchup on 2008-01-13
edrex, thanks for the tips, but I don't have anything at /usr/lib/xf86-input-evtouch.

---

### Post by edrex on 2008-01-14
Ok, evidently it's not installed by default:
```
sudo aptitude install  xserver-xorg-input-evtouch
```

---

### Post by lifeisbetterwithketchup on 2008-01-16
I got this when I ran the calibrate script.
```
colin@lifebook:/usr/lib/xf86-input-evtouch$ sudo ./calibrate.sh
./ev_calibrate
evalibrate located at ./ev_calibrate
xinit located at /usr/bin/xinit
xserver located at /usr/bin/X
Creating FIFO...
Starting calibration program...

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.

```

---

### Post by evilnebby on 2008-03-16
This is semi-working on my B-2562. Since this thread is recent I thought I´d give it a shot. Has anyone gotten this to work recently? I was able to run the calibration utility, but nothing happens in the first part where I´m supposed to trace the outer border of the screen. Manually tweaking the numbers has no effect either. If I cat /dev/input/mouse2 I get output when touching the screen. Movement across the entire screen vertically or horizontally moves the cursor proportionately about one fifth of the way across the screen originating in the top left corner. Any insight would be appreciated.

---

### Post by evilnebby on 2008-03-17
Since I don't want to be "that guy" who asks questions and doesn't follow through....

I was able to get my touchscreen calibrated in Linux using the instructions posted above. The problem was Linux is just too stable and the reload udev rules apparently wouldn't take until the system was rebooted. Why would I have to reboot in Linux? The thought hadn't occurred to me. So once I did, I was able to get some semi reasonable numbers out of the calibration program which had me set up in a jiffy. Hope this helps someone.

---

