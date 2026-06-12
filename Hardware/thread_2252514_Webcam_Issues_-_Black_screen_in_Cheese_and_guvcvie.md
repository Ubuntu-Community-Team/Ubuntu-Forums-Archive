---
title: "Webcam Issues - Black screen in Cheese and guvcview"
date: 2014-11-12
forum: Hardware
---

### Post by InsertNameHere345 on 2014-11-12
Hello,

I am currently in the preparation stages for my final year project at university and need a working webcam for an OpenCV application. I am running 14.04. However, when I open Cheese, all I find is a black screen. I have tried to receive video using guvcview also, but to no avail. The following is the output from dmesg after plugging the camera into a USB slot on the front of my system (you can see that I have done this several times):

```
[ 2128.933628] usb 1-1.1: USB disconnect, device number 5[ 2133.230578] usb 1-1.1: new high-speed USB device number 6 using ehci-pci
[ 2134.158155] usb 1-1.1: New USB device found, idVendor=1e4e, idProduct=0110
[ 2134.158160] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2134.158163] usb 1-1.1: Product: USB2.0 Camera
[ 2134.158165] usb 1-1.1: Manufacturer: Etron Technology, Inc.
[ 2134.163325] uvcvideo: Found UVC 1.00 device USB2.0 Camera (1e4e:0110)
[ 2134.168309] input: USB2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input24
[ 2370.963630] usb 1-1.1: USB disconnect, device number 6
[ 2374.233913] usb 1-1.1: new high-speed USB device number 7 using ehci-pci
[ 2375.161585] usb 1-1.1: New USB device found, idVendor=1e4e, idProduct=0110
[ 2375.161591] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 2375.161594] usb 1-1.1: Product: USB2.0 Camera
[ 2375.161596] usb 1-1.1: Manufacturer: Etron Technology, Inc.
[ 2375.166734] uvcvideo: Found UVC 1.00 device USB2.0 Camera (1e4e:0110)
[ 2375.171869] input: USB2.0 Camera as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input25



```

It appears to recognise the camera, however the information displayed using lsusb appears somewhat vague:

```
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 007: ID 1e4e:0110 Cubeternet 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



```

Is there anything that can be done to fix this issue? One of the requirements for the project was to use a CCD webcam which are awkward to find cheaply. However, some of the specs can be found on the retailer's site: [http://www.aliexpress.com/snapshot/6316843123.html](http://www.aliexpress.com/snapshot/6316843123.html)

Thank you for your help.

---

### Post by InsertNameHere345 on 2014-11-12
I have also ran guvcview in the terminal, which gave the following ouput. It appears that frames are not being grabbed for whatever reason:

```
(gstreamer-properties:6342): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:6342): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
brad@brad-To-be-filled-by-O-E-M:~$ guvcview
guvcview 1.7.1
file guvcview_video.mkv has extension type 1
file guvcview_image.jpg has extension type 0
file guvcview_image.jpg has extension type 0
Video file suffix detected: 2
Image file suffix detected: 0
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2239:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
video device: /dev/video0 
Init. USB2.0 Camera (location: usb-0000:00:14.0-3)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 480 }
	Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
	Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
	Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
	Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
	Time interval between frame: 1/30, 
vid:1e4e 
pid:0110 
driver:uvcvideo
checking format: 1448695129
fps is set to 1/30
drawing controls


fps is set to 1/30
Checking video mode 640x480@32bpp : OK 
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable



```

---

### Post by tatsujb on 2014-12-12
Same here. ubuntu 64bit 14.04 Microsoft (har-har) LifeCam Studio

cheese works, overlaying is on ffmpeg stream with video4linux2 works, outputing it with vlc, skype, teamviewer, google hangouts chats all work.

but all of these ever recieve is some low framerate 640x480 image:
```
t@tsu:~$ luvcview
luvcview 0.2.6

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
  Frame format: MJPG
  Frame size:   640x480
  Frame rate:   30 fps

```

video4linux control pannel works (albeit two errors on start)  ```

Unable to get menu item for Exposure, Auto, index=0

 Will use Unknown

Unable to get menu item for Exposure, Auto, index=2

 Will use Unknown
```
and indeed these two items apprear under "exposure" as "unkown" and cannot be used but I digress...

How can I configure my webcam to use it's full potential? E.G. 29.9 FPS @ 1920x1080

---

