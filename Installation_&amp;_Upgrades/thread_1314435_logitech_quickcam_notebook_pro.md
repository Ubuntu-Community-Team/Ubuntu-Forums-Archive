---
title: "logitech quickcam notebook pro"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by sakurazukamori on 2009-11-04
Hi to everyone, it seems that my webcam (logitech quickcam notebook pro) works no more under karmic koala 9.10
 (it was working perfectly under 9.04)
It's quite strange, I'll give you some output in order to find out what can be wrong :-\

```
$lsusb

Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 046d:08b1 Logitech, Inc. QuickCam Notebook Pro
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```


```
$guvcview

guvcview 1.1.1
bt_audio_service_open: connect() failed: Connessione rifiutata (111)
bt_audio_service_open: connect() failed: Connessione rifiutata (111)
bt_audio_service_open: connect() failed: Connessione rifiutata (111)
bt_audio_service_open: connect() failed: Connessione rifiutata (111)
video device: /dev/video0 
/dev/video0 - device 1
Init. Logitech QuickCam Notebook Pro (location: usb-0000:03:00.0-1)
{ pixelformat = 'PWC2', description = 'Raw Philips Webcam' }
   { not supported - request format(843274064) support at http://guvcview.berlios.de }
{ pixelformat = 'YU12', description = '4:2:0, planar, Y-Cb-Cr' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/5, 1/10, 1/15, 1/20, 1/25, 1/30, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/5, 1/10, 1/15, 1/20, 1/25, 1/30, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/5, 1/10, 1/15, 
checking format: 1196444237
Format unavailable: 1196444237.
Init v4L2 failed !! 
Init video returned -2
trying minimum setup ...
video device: /dev/video0 
/dev/video0 - device 1
Init. Logitech QuickCam Notebook Pro (location: usb-0000:03:00.0-1)
{ pixelformat = 'PWC2', description = 'Raw Philips Webcam' }
   { not supported - request format(843274064) support at http://guvcview.berlios.de }
{ pixelformat = 'YU12', description = '4:2:0, planar, Y-Cb-Cr' }
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/5, 1/10, 1/15, 1/20, 1/25, 1/30, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/5, 1/10, 1/15, 1/20, 1/25, 1/30, 
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/5, 1/10, 1/15, 
checking format: 842093913
Requested Format unavailable: get width 160 height 480 
Unable to set 5 fps
VIDIOC_S_PARM error: Argomento non valido
VIDIOC_QUERYBUF - Unable to query buffer: Argomento non valido
Init v4L2 failed !! 
ERROR: Minimum Setup Failed.
 Exiting...

```

Any idea? :-/

---

### Post by potatan on 2009-11-12
Hi,

I have a similar problem with "format not supported" - you can follow the thread here in case anything helps you:

[http://ubuntuforums.org/showthread.php?p=8301102#post8301102](http://ubuntuforums.org/showthread.php?p=8301102#post8301102)

---

