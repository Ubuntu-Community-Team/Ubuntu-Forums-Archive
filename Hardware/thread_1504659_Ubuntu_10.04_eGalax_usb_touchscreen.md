---
title: "Ubuntu 10.04 eGalax usb touchscreen"
date: 2010-06-08
forum: Hardware
---

### Post by Light Sighter on 2010-06-08
I have installed Ubuntu 10.04 Desktop edition on an Asus EeeBox B202 PC. Connected to it is a usb touch screen which appears in the usb list as a "D-WAV Scientific Co., Ltd eGalax TouchScreen":

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root huba
**Bus 002 Device 003: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen**
Bus 002 Device 002: ID 1241:1503 Belkin Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The touch screen out the box recognises a touch and I can therefore "Click". However, Ubuntu is not recognising where I touch the screen with the mouse cursor ending up in the top left-hand corner when I touch the screen.

Anyone have any insights into the issue I am having?

---

### Post by Stamat on 2010-06-08
I have the same problem... Trying to figure it out right now...

You should try this thread
[http://ubuntuforums.org/showthread.php?t=1478877]("http://ubuntuforums.org/showthread.php?t=1478877")[http://ubuntuforums.org/showthread.php?t=1478877](http://ubuntuforums.org/showthread.php?t=1478877)

And try to find something about TouchKit...

---

### Post by Light Sighter on 2010-06-08
Stamat,

Many thanks for the link to that thread. I have installed xserver-xorg-input-evtouch and created the conf file in xorg.conf.d directory. 

The touch screen cursor now moves and the calibration tool is working fully giving me min/max x/y back. However, after altering the file the cursor goes everywhere. 

What I do notice is that the calibrator is that it is now picking up two touch screen devices:

```
./xinput_calibrator_x11 --list
Device "EVTouch TouchScreen" id=11
Device "EVTouch TouchScreen" id=12

```

 I think I have read some where that, due to there being two, the calibrator might be picking the correct one by default. I will look further into this and post back with my progress.

---

### Post by Light Sighter on 2010-06-09
Stamat,

Update, Regarding the calibration, the reason why it was picking up two devices is because it was including the connected mouse for some reason. Once I figured out the correct device I selected this one for calibration and got the Min/Max X/Y. With this done, the cursor was still very jerky and inaccurate.

I then decided to manually adjust the Min and Max X/Y to the screen resolution with more success. The cursor now moved correctly, just with a huge offset to the right and under of my finger. Therefore, I went and adjusted the Min and Max values again and, after much twiddling, found the correct settings for my monitor with a default resolution of  1024 x 768. 

This is my config file as it stands now:

```
Section "InputClass"
Identifier "Touchkit Touch"
MatchIsTablet "on"
MatchDevicePath "/dev/input/event*"
Driver "evtouch"
Option "ReportingMode" "Raw"
Option "Emulate3Buttons"
Option "Emultate3Timeout" "50"
Option "SendCoreEvents" "On"
Option "TapTimer" "200"
Option "LongTouchTimer" "400"
Option  "MinX"          "0"
Option  "MaxX"          "4096"
Option  "MinY"          "0"
Option  "MaxY"          "4096"
EndSection

```I hope this helps you out Stamat.

---

### Post by macrules on 2010-08-13
hi guys,

I have been searching all the web to get my touch screen to work.
I have a device taht seems to be compatible with eGalax ( id 0dfc:0001 ) but I just can't get it working.

dmesg shows the usbtouchscreen driver being loaded.
Xorg shows it as some Win7-2touch thing, but it just does not respond.

Does anyone know how I could fix this?

---

