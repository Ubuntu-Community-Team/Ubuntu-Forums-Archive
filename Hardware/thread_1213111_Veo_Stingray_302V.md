---
title: "Veo Stingray 302V"
date: 2009-07-14
forum: Hardware
---

### Post by jarg on 2009-07-14
I have an old Veo Stingray 302V webcam that I've been trying to get to work, no luck. I've found lots of information but none that is recent.

some basic information

```

jared@jackalope-terminal:~$ lsusb
**Bus 001 Device 005: ID 0545:800d Xirlink, Inc. Veo PC Camera**
Bus 001 Device 002: ID 04d9:048e Holtek Semiconductor, Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jared@jackalope-terminal:~$ ls /dev/video*
**ls: cannot access /dev/video*: No such file or directory**

```

That second part might be a problem.

---

### Post by jarg on 2009-07-14
Alright, I have the camera recognized now by following this long unanswered question ([http://ubuntuforums.org/showthread.php?t=948598](http://ubuntuforums.org/showthread.php?t=948598))

```

jared@jackalope-terminal:~$ sudo modprobe ibmcam
jared@jackalope-terminal:~$ ls /dev/video*
/dev/video0

```

Skype (the reason I'm trying this) crashes when I use their video device test.

According to this ([http://www.linux-usb.org/ibmcam/#VeoStingray_Note](http://www.linux-usb.org/ibmcam/#VeoStingray_Note)) note on the ibmcam page a person was able to apply a hack to make my same camera work, but I can't replicate it because I don't have the file he altered ("/usr/src/linux/drivers/usb/ibmcam.c").

Edit:

I've downloaded a couple programs to see what errors they spit out.
Camorama gives a dialogue box error that says 

> Could not connect to video device (/dev/video0).
Please check connection.
Nothing in the terminal and it just quits. BTW, those sorts of errors should have copyable text.

Camstream is more interesting, it actually gives a picture. The picture was blue so I attempted to go to display/color settings and change them, my computer froze and my keyboard LEDs started flashing (is that a kernel panic, I'm not sure). Forced restart, had to rerun modprobe, reopened camstream and messed with colors (couldn't fix them, just got black and white), no freezing this time.

Any clues how to fix the colors and get it running in Skype?

Here's a picture from camstream ([http://imgur.com/JAOqJ.png](http://imgur.com/JAOqJ.png)), that is a white door under a mix of fluorescent and incandescent lights.

---

### Post by jarg on 2009-07-15
I've managed to find a program to can have its settings tweeked for color, "Gqcam." When I open it I have to turn "Autoscale brightness" off, it just keeps going around forever if I don't, and change filters so "RGB -> BGR Conversion" is selected and "RGB" is selected. I then make all options on the main window 128.

gqcam "Camera -> camera info"
```

Name: IBM USB Camera
Type: 1
     Can Capture
Channels: 1
Audios: 0
Maxwidth: 352
Maxheight: 288
Minwidth: 8
Minheight: 4
---------
X: 0
Y: 0
Width: 352
Height: 288
Chromakey: 0
Flags: -1
---------
Brightness: 32768 (128)
Hue: 32768 (128)
Color: 32768 (128)
Contrast: 32768 (128)
Whiteness: 26880 (105)
Depth: 24
Palette: 4 - RGB24

```

Now I know what settings I need on the camera. Can anyone tell me how to make these default for all programs, how to make the modprobe happen every boot, and how to get skype not to crash?

---

### Post by jarg on 2009-07-15
Okay I have it working in skype i followed this guide ([http://ubuntuforums.org/showthread.php?t=725179](http://ubuntuforums.org/showthread.php?t=725179)) and made one small change to his script (is it necessary to use sudo for modprobe?).

Strangely just having gstfakevideo use the webcam without going through effectv doesn't work.

```

#!/bin/bash
#
# setup gstfakevideo preload to hijack calls made
# to /dev/video0
#
#This script runs Skype with libskype_dsp_hijacker.so "filter"
#It allows redefining of what devices Skype uses for 
#microphone, speakers and mixer (especially microphone and
#speakers can use different devices)

[b]#Load imbcam in order to recognize Veo Stingray 302V
#I assume any webcam that uses ibmcam will work with this.
sudo modprobe ibmcam[/b]

# -- CONFIGURATION --

#default configuration when no option is specified

export HIJACKVIDEO="/dev/video0"
export GST_PIPE="v4lsrc device=/dev/video2 ! ffmpegcolorspace"  

prefix=/usr/local
exec_prefix=${prefix}

#prefer use of libskype_dsp_hijacker from current directory
if test -f ./libgstfakevideo.so; then 
  libdir=.
else
  libdir=${exec_prefix}/lib
fi

LD_PRELOAD=${libdir}/libgstfakevideo.so
if test -f /lib/libdl.so.2; then
	LD_PRELOAD=$LD_PRELOAD:/lib/libdl.so.2
fi
export LD_PRELOAD


#Move current webcam over to /dev/video3

if test -e /dev/video0; then 
  sudo mv /dev/video0 /dev/video3
fi


# load vloopback module first

sudo modprobe vloopback

# invoke effectv first, and give it a second to load

effectv -device /dev/video3 -vloopback /dev/video1 &

sleep 1

exec skype

```

I have one small problem now. The image in the effectv window does not match what skype sees, skype's colors are off (without any effects).

I think the problem is gstfakevideo is doing something weird with the vloopback output (because effectv gets it right). Does anyone know how I could fix this?

---

