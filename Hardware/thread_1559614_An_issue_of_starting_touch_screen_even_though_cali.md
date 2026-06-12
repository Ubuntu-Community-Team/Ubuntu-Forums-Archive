---
title: "An issue of starting touch screen even though calibration has been completed"
date: 2010-08-23
forum: Hardware
---

### Post by jingpro on 2010-08-23
Hello,

I installed Ubuntu Netbook 10.04 on my eee pc 900HA. I also downloaded the touch screen calibration utility from [here]("http://github.com/downloads/tias/xinput_calibrator/xinput-calibrator_0.7.0-ubuntu1_i386.deb"). 

I ran the utility, calibrated the touch screen successfully, and got following result:

> Calibrating EVDEV driver for "eGalax Inc. USB TouchController" id=10
	current calibration values (from XInput): min_x=117, max_x=1951 and min_y=1833, max_y=156

Doing dynamic recalibration:
	Setting new calibration data: 108, 1956, 1831, 164


== Saving the calibration ==
If you have the 'xinput' tool installed, a simple way is to create a script that starts with your X session, containing the following command(s):
    xinput set-int-prop "eGalax Inc. USB TouchController" "Evdev Axis Calibration" 32 108 1956 1831 164
See scripts/xinput_calibrator_pointercal.sh for an example used on mobile devices

If you have evdev version 2.3.0 or higher, there are 2 more ways: the tranditional way (xorg.conf) and the new way (udev rule):
xorg.conf: edit /etc/X11/xorg.conf and add in the 'Section "InputDevice"' of your device:
    Option	"Calibration"		"108 1956 1831 164"
udev rule: create the file '/etc/udev/rules.d/99_touchscreen.rules' with:
    ACTION!="add|change", GOTO="xorg_touchscreen_end"
    KERNEL!="event*", GOTO="xorg_touchscreen_end"
    ATTRS{product}!="eGalax Inc. USB TouchController", GOTO="xorg_touchscreen_end"
    ENV{x11_options.calibration}="108 1956 1831 164"
    LABEL="xorg_touchscreen_end"


Based on this, I created a file of '99_touchscreen.rules'.

Now I restart the computer, but the touch screen is still non-calibrated. I have to do calibration again.

Anyone can tell me how to correct this issue? Thanks a lot.

---

### Post by jingpro on 2010-08-24
Anyone can help me?

---

