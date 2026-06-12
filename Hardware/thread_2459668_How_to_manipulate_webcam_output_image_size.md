---
title: "How to manipulate webcam output image size?"
date: 2021-03-23
forum: Hardware
---

### Post by antoniobuntu on 2021-03-23
Hi
is there any way to shrink (kind of zoom in) the output of the preinstalled camera?
I ask this because I am going to participate in a webinar and the application they are using for video conference gives out an image / video where my face appears very close to the camera and so it occupies the whole space needed to show the presenter, and of course parts of the face remain out of the video "square".
Of course I could simply move my computer further away but then I won't be able to interact easily with the keyboard, or my voice might not be heard clearly (ok I could headphones with mike attached)
So I wonder if there is any software that allows to control the size of the camera output
I am using ubuntu 20.4 
Thanks in advance

---

### Post by TheFu on 2021-03-23
Camera hardware has supported resolutions. Those are what you see in the different webcam tools.  You can use software zoom to change what gets displayed by a webcam. Zoom and brightness control examples:
```
v4l2-ctl -d /dev/video0 -c zoom_absolute=200
v4l2-ctl -d /dev/video0 -c brightness=100
```

By changing the zoom, you can probably solve the huge nose/head issue.
Good news is that v4l2 control commands can be run outside whatever tool is being used for the video conference. Probably want to play around with this for 10-30 minutes.

I'm making assumptions, like 
[LIST]
[*]the webcam is supported by v4l2
[*]video0 is the device - it could be video1, 2, 3, 4, 5, 6.... just ll in /dev/vide* to see the options. Usually there is only 1.
[*]Change the zoom value from say - 50 to 500 to see where the limits are. Different cameras/software supports different zoom amounts. In theory 100 is the default, normal, zoom.
[/LIST]

Update: corrected v2l2 --> v4l2
v4l2 is "Video For Linux v2"

---

### Post by antoniobuntu on 2021-03-23
Hi, thanks for suggesting the use of v4l2-ctl.
I tried the command 'with zoom_absolute' but it doesn't seem to recognize the 'zoom_absolute" parameter
How do I know if the webcam is supported by v2l2?
I have 2 video devices 0 & 1. I tried the command on both but get the same result

---

### Post by TheFu on 2021-03-23
It is highly unlikely that any webcam which works on Linux **doesn't** support v4l2 (sorry for my typo above.  V4L2, not V2L2)
Maybe show the exact command used?  And any errors shown.

The manpage for v4l2-ctl should have lots of other control options/parameters. Do those work and just zoom doesn't?

---

### Post by antoniobuntu on 2021-03-23
The commando used is:

```
~$ v4l2-ctl -d /dev/video0 -c zoom_absolute=200 
```

Error message: unknown control 'zoom_absolute'

Also, when I run the command:
```
v4l2-ctl --list-ctrls
```
The result is:

brightness 0x00980900 (int)    : min=-64 max=64 step=1 default=0 value=64
    contrast 0x00980901 (int)    : min=0 max=64 step=1 default=32 value=32
 saturation 0x00980902 (int)    : min=0 max=128 step=1 default=64 value=64
          hue 0x00980903 (int)    : min=-180 max=180 step=1 default=0 value=0
white_balance_temperature_auto 0x0098090c (bool)   : default=1 value=1
     gamma 0x00980910 (int)    : min=100 max=500 step=1 default=220 value=220
power_line_frequency 0x00980918 (menu)   : min=0 max=2 default=1 value=1
white_balance_temperature 0x0098091a (int)    : min=2800 max=6500 step=10 default=4650 value=4650 flags=inactive
  sharpness 0x0098091b (int)    : min=0 max=8 step=1 default=4 value=4
backlight_compensation 0x0098091c (int)    : min=0 max=1 step=1 default=0 value=0
exposure_auto 0x009a0901 (menu)   : min=0 max=3 default=3 value=1
exposure_absolute 0x009a0902 (int)    : min=155 max=10000 step=1 default=310 value=155


So there seem to be not any control for zoom shown here.

---

### Post by TheFu on 2021-03-23
Is there another device? Got the right one?
Perhaps the device doesn't support zoom?

On my laptop, it doesn't support zoom.  Changing resolutions doesn't help either.  
On a desktop, with a USB webcam, it does.  I know the c270 and c920 models do. Both ar plug-n-play on ubuntu. They are cheap again - even less than pre-covid.

Might be able to use OBS in the middle between the app and the camera.

---

### Post by antoniobuntu on 2021-03-24
> **TheFu said:**
> Is there another device? Got the right one?
Perhaps the device doesn't support zoom?
How do I verify these?

> **TheFu said:**
>  Might be able to use OBS in the middle between the app and the camera.
What is OBS?

By the way I just discovered that the other controls are not recognized either! How can this be?
I tried 'brightness' and received the the same error message: 'unknown control'

---

### Post by TheFu on 2021-03-24
> **antoniobuntu said:**
> How do I verify these?
ls /dev/vide*

> **antoniobuntu said:**
> 
What is OBS?
Did google not have an answer?   Open Broadcast Software/System?  It is THE go-to F/LOSS tool for video processing and live production on most platforms.  OBS can get multiple inputs for video and audio, then do some processing and mux those into a single output which can be saved to a file, streamed on the network, passed to a normal video input for some other program ... like video conferencing. It is infinitely configurable, so taking a class might be needed to grasp all it can do.  Some capabilities are non-trivial to use and require building kernel modules, but many are easy. It can definitely scale, crop, zoom inputs.  Of course there is a price for OBS - it likes RAM and CPU. I've run it find for simple muxing of 2 video and 1 audio source on Core i3, but much more than that and more CPU is needed.

> **antoniobuntu said:**
> 
By the way I just discovered that the other controls are not recognized either! How can this be?
I tried 'brightness' and received the the same error message: 'unknown control'
Unpopular or bad hardware? IDK.

Seems we've exhausted my ability to help. Sorry. I wish you luck.

---

