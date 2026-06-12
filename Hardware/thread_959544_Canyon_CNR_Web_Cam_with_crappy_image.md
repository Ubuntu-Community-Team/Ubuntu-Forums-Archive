---
title: "Canyon CNR Web Cam with crappy image"
date: 2008-10-26
forum: Hardware
---

### Post by Mr.nano on 2008-10-26
Hi all, I have this problem and after looking for solutions now I'm stuck and need help.

What I got is Canyon CNR-WCAM413 (1.3M pixels usb web camera)
What I want to do is: Watch and Capture Video

I use hardy 8.04 and the camera is recognized by lsusb as:
Device 002: ID 0ac8:0323 Z-Star Microelectronics Corp. Luxya WC-1200 USB 2.0 Webcam

In skype's options at video devices I clicked the buttop to test the camera and i see the video it captures - so the camera is working out of the box. (VC0323 /dev/video0)

I've installed a couple of applications:

luvcview - it pops up with that error:
luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
Error opening device /dev/video0: unable to query device.
 Init v4L2 failed !! exit fatal 


camorama - it show image but it is terribly awful with green-like colors, in small window and with terrible resolution. In view menu as I click the large option it breaks with this error: unable to capture image.

v4l-info gives this:
### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
	name                    : "VC0323"
	type                    : 0x1 [CAPTURE]
	channels                : 1
	audios                  : 0
	maxwidth                : 640
	maxheight               : 480
	minwidth                : 320
	minheight               : 240

channels
    VIDIOCGCHAN(0)
	channel                 : 0
	name                    : "VC0323"
	tuners                  : 0
	flags                   : 0x0 []
	type                    : CAMERA
	norm                    : 0

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
	brightness              : 32768
	hue                     : 0
	colour                  : 0
	contrast                : 32768
	whiteness               : 0
	depth                   : 24
	palette                 : RGB24

buffer
    VIDIOCGFBUF
	base                    : (nil)
	height                  : 0
	width                   : 0
	depth                   : 0
	bytesperline            : 0

window
    VIDIOCGWIN
	x                       : 0
	y                       : 0
	width                   : 640
	height                  : 480
	chromakey               : 0
	flags                   : 0

So how can I adjust to see the video in larger window and make the camera to capture with 1.3 MPixs and to have better quality as in camorama all the sliders seems not working and give no change to the picture at all?

How to see if this camera is using the proper drivers?

---

### Post by Plexor on 2009-04-18
Im having troubles with this camera also.  Colors are all messed up, otherwise the cam works great!

---

