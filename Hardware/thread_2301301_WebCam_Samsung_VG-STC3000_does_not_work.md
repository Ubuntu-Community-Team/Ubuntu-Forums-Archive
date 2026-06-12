---
title: "WebCam Samsung VG-STC3000 does not work"
date: 2015-11-01
forum: Hardware
---

### Post by olman2 on 2015-11-01
WebCam is defined as **04e8: 205c**
Anyway program Cheese, guvcview can not work with it.
The specifications of Samsung stated:
Chip AIT8453;
Embedded 32-bit CPU / 500MHZ
On-Chip ISP up to 8MP
MJPEG 1080P @ 30fps
H.264 1080P @ 30fps
Built-in
- I2S interface
- USB2.0
Compliant with UVC 1.0 / 1.1 and UAC 1.0

v4l2-ctl --all issues:
Driver name: uvcvideo
Card type: USB2.0 UVC HQ WebCam
Bus info: usb-0000: 00: 1d.7-4
Driver version: 3.19.8
Capabilities: 0x84200001
Video Capture
Streaming
Device Capabilities
Device Caps: 0x04200001
Video Capture
Streaming
Priority: 2
Video input: 0 (Camera 1: ok)
Format Video Capture:
Width / Height: 640/480
Pixel Format: 'YUYV'
Field: None
Bytes per Line: 1280
Size Image: 0
Colorspace: SRGB
Custom Info: feedcafe
Crop Capability Video Capture:
Bounds: Left 0, Top 0, Width 640, Height 480
Default: Left 0, Top 0, Width 640, Height 480
Pixel Aspect: 1/1
Streaming Parameters Video Capture:
Capabilities: timeperframe
Frames per second: invalid (1/0)
Read buffers: 0
Information on the Internet is not found ...:(

---

