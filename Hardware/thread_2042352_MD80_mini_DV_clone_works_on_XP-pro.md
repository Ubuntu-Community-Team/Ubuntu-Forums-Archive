---
title: "MD80 mini DV clone works on XP-pro"
date: 2012-08-14
forum: Hardware
---

### Post by gobbyteacher on 2012-08-14
... but not on ubuntu. I will NOT give up...

ok folks, I'm trying to get a clone MD80 working. Here's the details so far:

terminal work:

1. plug the camera in, the file explorer opens the 2gb sim card.

2. ls /dev/video* sez no such file or directory. After presssing buttons I find a short press of the power button closes the file explorer and ls /dev/video* now gives me /dev/video0

3. lsusb reveals this:
Bus 001 Device 005: ID 1b3f:2002 Generalplus Technology Inc.

4. hwinfo --usb reveals this:
11: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: X7GA.QWL_zlewMKE
  Parent ID: k4bc.9T1GDCLyFd9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0
  SysFS BusID: 1-7:1.0
  Hardware Class: unknown
  Model: "GENERAL - UVC"
  Hotplug: USB
  Vendor: usb 0x1b3f "GENERAL"
  Device: usb 0x2002 "GENERAL - UVC"
  Revision: "1.00"
  Driver: "uvcvideo"
  Driver Modules: "uvcvideo"
  Device File: /dev/input/event5
  Device Files: /dev/input/event5, /dev/input/by-id/usb-GENERAL_GENERAL_-_UVC-event-if00, /dev/input/by-path/pci-0000:00:1d.7-usb-0:7:1.0-event
  Device Number: char 13:69
  Speed: 480 Mbps
  Module Alias: "usb:v1B3Fp2002d0100dcEFdsc02dp01ic0Eisc01ip00"
  Driver Info #0:
    Driver Status: uvcvideo is active
    Driver Activation Cmd: "modprobe uvcvideo"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #3 (Hub)

app results:

5. guvcview fires up, gives me various messages, then I get:

vid:1b3f 
pid:2002 
driver:uvcvideo
checking format: 859981650
fps is set to 1/30
drawing controls

fps is set to 1/1
Checking video mode 720x480@32bpp : OK 
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable etc etc

6. mplayer gives me this:
mplayer -fps 30 -cache 128 -tv driver=v4l2:width=640:height=480:device=/dev/video0 tv://
...(edited)...TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: GENERAL - UVC 
 Capabilities:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: MJPEG
v4l2: ioctl set format failed: Invalid argument ...(repeat 6 times)...
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
v4l2: ioctl query control failed: Invalid argument...(repeat 3 times)
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
libavcodec version 53.35.0 (external)
Mismatching header version 53.32.2
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG)
==========================================================================
Audio: no sound
FPS forced to be 30.000  (ftime: 0.033).
Starting playback...
v4l2: select timeout
v4l2: select timeout
v4l2: select timeout
v4l2: select timeout
V:   0.0   9/  9 ??% ??% ??,?% 0 0 0% 
v4l2: select timeout
V:   0.0  11/ 11 ??% ??% ??,?% 0 0 0% 
v4l2: select timeout
V:   0.0  13/ 13 ??% ??% ??,?% 0 0 0% ...(repeat until ctrl-c)...

7. Gstreamer-properties gives me video for Linux 2 (v4l2) as the only plugin, device is a choice of GENERAL-UVC or default, testing just gives me a panel saying testing... click ok to finish.

8. VLC just gives me the orange traffic cone:
vlc v4l2:///dev/video0

Things I've tried:

9. reinstalled and checked good, bad and ugly libraries.

10. installed wxcam and tried all permutations of frame/driver (this app also gives me the option to try video4linux 1 and 2) - no go.

11. updated/rebuilt drivers as per
[http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/](http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/)

12. tried cheese etc. no go.

13. fired up MS XP-pro and the sodding thing works right off the bat... Grr.

Ok, I' DON'T want to give up on linux, but if it'll work with xp-pro then surely it'll work with Ubuntu 12.04

Any and all ideas gratefully received...

---

### Post by FakeOutdoorsman on 2012-08-14
Have you tried the steps listed here? [How to capture a webcam input](https://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20capture%20a%20webcam%20input).

Possibly related (older) thread: [Anyone have one of the Chinese MD80 clone MiniDV cameras working as a webcam?](http://ubuntuforums.org/showthread.php?t=1391735)

---

### Post by gobbyteacher on 2012-08-15
ok tried the stuff on [https://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20capture%20a%20webcam%20input](https://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20capture%20a%20webcam%20input)

this gave me the following:

~$ ffmpeg -f video4linux2 -r 25 -s 640x480 -i /dev/video0 pc_temp.avi
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[video4linux2 @ 0x8487240] The V4L2 driver changed the video from 640x480 to 720x480
[video4linux2 @ 0x8487240] The driver changed the time per frame from 1/25 to 1/30
^C

which sits there until I ctrl-c.

I did notice that the ffmpeg page suggested v4l2-ctl to get more info on the camera, so I installed, ran and got the following:

$ v4l2-ctl --all
Driver Info (not using libv4l2):
	Driver name   : uvcvideo
	Card type     : GENERAL - UVC 
	Bus info      : usb-0000:00:1d.7-7
	Driver version: 3.2.24
	Capabilities  : 0x04000001
		Video Capture
		Streaming
Format Video Capture:
	Width/Height  : 720/480
	Pixel Format  : 'MJPG'
	Field         : None
	Bytes per Line: 0
	Size Image    : 614400
	Colorspace    : Unknown (00000000)
Crop Capability Video Capture:
	Bounds      : Left 0, Top 0, Width 720, Height 480
	Default     : Left 0, Top 0, Width 720, Height 480
	Pixel Aspect: 1/1
Video input : 0 (Camera 1: ok)
Streaming Parameters Video Capture:
	Capabilities     : timeperframe
	Frames per second: 30.000 (30/1)
	Read buffers     : 0

and thanks for the other link but that's where I started and tried all, including the reformat sd card/reset.

Keep the suggestions coming!

---

