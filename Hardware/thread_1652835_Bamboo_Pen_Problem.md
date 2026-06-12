---
title: "Bamboo Pen Problem"
date: 2010-12-25
forum: Hardware
---

### Post by klapointe on 2010-12-25
I got a Bamboo Tablet "Pen" just last night. It is the CTL-460/K style.

I followed the instructions on the howto for Bamboo tablets and when I run the .sh file for the tablet, nothing happens. 

When I insert xsetwacom --list in to terminal, this is the response:

```
Wacom Bamboo 4x5 Pen eraser         id: 9    type: ERASER    
Wacom Bamboo 4x5 Pen stylus         id: 10    type: STYLUS    
Wacom Bamboo 4x5 Finger pad         id: 11    type: PAD       
Wacom Bamboo 4x5 Finger touch       id: 12    type: TOUCH    
```

So in my .xsetwacom.sh file, this is what it says.

```
## Device names and ID numbers from 'xinput --list' entered in a terminal.
#
## In the example both "Device name" and ID # are used.  Note if you use the
## xorg.conf the "Device names" will be stylus, eraser, touch, and pad.
#
## If you are hot plugging use "Device name" as ID # can change.
#
## ClickForce changes name to Threshold with xf86-input-wacom 0.10.9 (11-19-10)
## Lucid default - 0.10.5  Maverick default - 0.10.8
#
## Warning:  Changing Mode to either Absolute or Relative in stylus/eraser stops
## the mouse from being able to pull guidelines out of the ruler in Gimp.

## stylus = ID 10 = "Wacom Bamboo 4x5 Pen stylus"
xsetwacom set "Wacom Bamboo 4x5 Pen stylus" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "Wacom Bamboo 4x5 Pen stylus" RawSample "2"  # data pt.s filtered, default is 2, 0-100
#xsetwacom set "Wacom BambooFun 2FG 4x5 Pen stylus" ClickForce "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "Wacom Bamboo 4x5 Pen stylus" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set 10 PressCurve "5 10 90 95"  # Bezier curve, default is 0,0,100,100
xsetwacom set 10 TPCButton "on"  # stylus tip + button, or "off" for hover mode
#xsetwacom set 10 Mode "Absolute"  # or "Relative" cursor movement
xsetwacom set 10 Button1 "1"  # left mouse click
xsetwacom set 10 Button2 "3"  # right mouse click
xsetwacom set 10 Button3 "2"  # middle mouse click

## eraser = ID 9 = "Wacom Bamboo 4x5 Pen eraser"
xsetwacom set 9 Suppress "4"  # data trimmed, default is 4, 0-20
xsetwacom set 9 RawSample "2"  # default is 2, 0-100
#xsetwacom set 9 ClickForce "27"  # pressure, default is 27, range is 0-2047
xsetwacom set 9 Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set 9 PressCurve "0 10 90 100"  # Bezier curve, default is 0,0,100,100
#xsetwacom set 9 Mode "Absolute"  # or "Relative" cursor movement
xsetwacom set 9 Button1 "1"

## touch = ID 12 = "Wacom Bamboo 4x5 Finger touch"
xsetwacom set "Wacom Bamboo 4x5 Finger touch" Touch "on"  # or "off"
xsetwacom set "Wacom Bamboo 4x5 Finger touch" Gesture "on"  # or "off"
xsetwacom set "Wacom Bamboo 4x5 Finger touch" Suppress "4"  # data trimmed, default is 4, 0-20
xsetwacom set 12 RawSample "2"  #  efault is 2, 0-100
#xsetwacom set 12 ClickForce "27"  # default is 27, range is 0-2047
xsetwacom set 12 Threshold "27"  # default is 27, range is 0-2047
xsetwacom set 12 Mode "Relative"
# 1FG dbl. tap is left click, 2FG dbl. tap is right click
xsetwacom set 12 ZoomDistance "50"  # default is 50
xsetwacom set 12 ScrollDistance "20"  # default is 20
xsetwacom set 12 TapTime "250"  # 2FG R click, default is 250 ms

## pad = ID 11 = "Wacom Bambo 4x5 Finger pad"
xsetwacom set 11 Button1 "shift ctrl t"  # toggle touch script
xsetwacom set 11 Button2 "shift backspace"
xsetwacom set 11 Button3 "3"  # right mouse click
xsetwacom set 11 Button4 "shift alt left"  # Back a page in FireFox

## Developed with dr4ziw and iRi_E
```

I have no idea if that is causing any problems or stopping it from working properly. I cannot use the wacom on anything- is the wacom screen always supposed to be black?

I've never used a tablet before so I have no idea how it is supposed to work.

I use Gimp and I am trying to get it to work on gimp, but whenever I activate the .sh file, it stops the mouse from doing anything on the screen except for clicking pencil, paint, etc, and scrolling around the top. I can't actually paint or draw on the field of the page. As for the tablet, nothing happens when I touch it with the pen.

How can I get it to work on at least Gimp? I probably won't use it for anything else except drawing on Gimp.

Any help will be appreciated.

---

### Post by Favux on 2010-12-26
Hi klapointe,

If it is the pen you should only have the stylus with two buttons.  If so you can remove the eraser, touch, and pad sections from the script.

Did you update the wacom.ko to the linuxwacom 0.8.8-10 version?  And clone the git repository for the latest xf86-input-wacom X driver?

Let's check your product ID.  Enter in a terminal:
```
lsusb
```
and post the Wacom line.

---

### Post by klapointe on 2011-01-17
Alright, I have the two buttons on the Pen, so I deleted those sections.

The output for "lsusb" is

```
Bus 002 Device 015: ID 056a:00d4 Wacom Co., Ltd 
Bus 002 Device 013: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Sorry for the late response. I've been a bit busy.

---

### Post by Favux on 2011-01-17
Well it is the right model:
```
Bus 002 Device 015: ID 056a:00d4 Wacom Co., Ltd
```
The Vendor ID = 056a (i.e. Wacom) Product ID = 00d4 (i.e. Bamboo Pen).  So what I said about the script is correct.  You are using the right "Device name" in the stylus section of the script, which is all you need.

Does the stylus move the pointer around on the screen?

Let's make sure your wacom.ko is autoloading.  Enter in a terminal:
```
lsmod | grep wacom
```

For Gimp you have to configure your extended input device, in your case it would be the stylus.  See near the end of the Wacom wiki:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)

---

