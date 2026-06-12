---
title: "After replugging Logitech Quickcam for Notebook Pro 046d:08c3 is not recognised"
date: 2008-08-18
forum: General Help
---

### Post by jreinis on 2008-08-18
Skype write: Previuos webcam not detected /dev/video0

Some time 
lsusb shows after FIRST PLUG of USB webcam
Bus 007 Device 002: ID 046d:08c3 Logitech, Inc.
After REPLUGGING 
lsusb shows or top number
Bus 007 Device 003: ID 046d:08c3 Logitech, Inc.
or just it disappears!

Who can explain how to stop change device number for USB devices or where is disappeared the webcam? :confused:

 uname -a
Linux main-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux


 modinfo uvcvideo
filename: /lib/modules/2.6.24-16-generic/ubuntu/media/usbvideo/uvcvideo.ko
version: SVN r240
license: GPL
description: USB Video Class driver
author: Laurent Pinchart <laurent.pinchart@skynet.be>
srcversion: 471124299D0746FA9FA44EA
alias: usb:v*p*d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v5986p0303d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v5986p0300d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v5986p0200d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v5986p0141d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v5986p0102d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v5986p0101d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v5986p0100d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v1C4Fp3000d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v19ABp1000d00*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v19ABp1000d01[0-1]*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v19ABp1000d012[0-6]dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v18CDpCAFEd*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v174Fp8A33d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v174Fp8A31d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v174Fp5212d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v0E8Dp0004d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v090CpB371d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v05E3p0505d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v05ACp8501d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v046Dp08C7d*dc*dsc*dp*icFFisc01ip00*
alias: usb:v046Dp08C6d*dc*dsc*dp*icFFisc01ip00*
alias: usb:v046Dp08C5d*dc*dsc*dp*icFFisc01ip00*
alias: usb:v046Dp08C3d*dc*dsc*dp*icFFisc01ip00*
alias: usb:v046Dp08C2d*dc*dsc*dp*icFFisc01ip00*
alias: usb:v046Dp08C1d*dc*dsc*dp*icFFisc01ip00*
alias: usb:v045Ep0723d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v045Ep00F8d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v041Ep4057d*dc*dsc*dp*ic0Eisc01ip00*
alias: usb:v0402p5606d*dc*dsc*dp*ic0Eisc01ip00*
depends: usbcore,videodev,v4l2-common,v4l1-compat,compat_ioctl32
vermagic: 2.6.24-16-generic SMP mod_unload
parm: quirks:Forced device quirks (uint)
parm: trace:Trace level bitmask (uint) 

lsmod | grep uvcvideo
uvcvideo               63752  0 
compat_ioctl32         11136  1 uvcvideo
videodev               30720  1 uvcvideo
v4l1_compat            15492  2 uvcvideo,videodev
v4l2_common            21888  3 uvcvideo,compat_ioctl32,videodev
usbcore               169904  9 uvcvideo,usblp,snd_usb_audio,snd_usb_lib,usb_storage,libusual,ehci_hcd,uhci_hcd

---

