---
title: "How to read output data from Webcam"
date: 2013-11-23
forum: Hardware
---

### Post by james30 on 2013-11-23
I am using VMWare Workstation and running Ubuntu 12.04LTS and am kind of a beginner
I was wondering how to read data output of a webcam..

So far I have got webcam working with 'Cheese' and found /dev/video0 (if it is related to this matter)
But that's as far I have gone in terms of reading this data.

It won't matter what kind of data, just any sort of data that I maybe able to sort it into an image using C..

I tried opening video0 file with permission, but there seems to be no applications I can open with.
Also it is registered with 0 bytes..
This file also only appears when the USB webcam is plugged in (Microdia USB 2.0 SONIX).

Help would be much appreciated!
:D

---

### Post by ksprasad on 2013-11-23
Hi,

Im not exactly sure what you are trying to do. But a simple program like below can be written to read the data from webcam. (not sure if it works as i didn't test it).
```

#include <stdio.h>
#include <stdlib.h>
int main() {
  FILE *camLive, *out;
  float data[640*480];
  camLive=fopen("/dev/video0", "rb");
  out=fopen("outfile", "wb");
  fread(data, sizeof(data[0]), 640*480, camLive);
  fwrite(data, sizeof(data[0]), 640*480, out);
  fclose(camLive);
  fclose(out); 
  return 0;
}

```

Regards,
ksprasad

---

### Post by tgalati4 on 2013-11-23
Here's a list to work through.  If any of these tools are helpful, then look at the source code.  No need to rewrite what has been done.


tgalati4@tpad-Gloria7 ~ $ apt-cache search webcam
came - Rewrite of the xawtv webcam app using imlib2
cameramonitor - Webcam monitoring in system tray
camgrab - A command line tool to download a single image from a webcam
camorama - gnome utility to view and save images from a webcam
camstream - collection of tools for webcams and other video-devices
camstream-doc - documentation for CamStream
cheese - A tool to take pictures and videos from your webcam
feh - imlib2 based image viewer
geekast - GNOME interface to peercast
geekast-binary - GNOME interface to peercast - binaries
gkrellkam - GKrellM plugin that displays a periodically updating image
gmotionlive - A simple multipart/x-mixed-replace viewer
gqcam - GTK Webcam control
gspca-source - source for the gspca v4l kernel module
libdecodeqr-dev - A C/C++ library for decoding QR code
libdecodeqr-examples - Sample program in C/C++ library for decoding QR code
libdecodeqr0 - A C/C++ library for decoding QR code
luvcview - USB Video Class grabber
lynkeos.app - Tool to process planetary astronomical images for GNUstep
motion - V4L capture program supporting motion detection
ov51x-jpeg-source - Source for the ov51x-jpeg driver
peercast-geekast - GNOME interface to peercast - peercast-servent data files
pymissile - Control Marks and Spencer USB Missile Launcher
pyrocket - control Striker II and Dream Cheeky USB Missile Launchers
qc-usb-source - source for the QuickCam Express driver
qc-usb-utils - utility programs for the QuickCam Express driver
setpwc - program to set and query settings of (mainly) Philips WebCams
telak - display remote or local pictures on your desktop
uvccapture - USB UVC Video Class snapshot software
vgrabbj - grabs a image from a camera and puts it in jpg/png format
webcam - image grabber and uploader
webcam-server - a tool to share webcam streaming in www-browser
webcamd - Capture images from video devices
zebra-tools - scanning and decoding bar codes (utilities)

---

### Post by james30 on 2013-11-24
Thanks for replying,

I was just wondering why couldn't I open the /dev/video0 and view it?
But you can fopen using C?

---

