---
title: "Logitech Quickcam Sphere not working in Ubuntu Karmic but used to work in previous"
date: 2010-04-27
forum: Hardware
---

### Post by GeoMX on 2010-04-27
I've got a Logitech Quickcam Sphere webcam, sometime ago, when using a previous Ubuntu version (don't remember which one) this camera worked out of the box. But now, trying to use it in Karmic, it does not work. When plugged a new /dev/video1 appears (video0 is my laptop's internal webcam), lsusb lists it correctly:

lsusb | grep Logitech:
> 
Bus 005 Device 005: ID 046d:08b5 Logitech, Inc. QuickCam Sphere


dmesg:
> 
[ 4975.288165] usb 5-1: new full speed USB device using uhci_hcd and address 5
[ 4976.124479] usb 5-1: configuration #1 chosen from 1 choice
[ 4976.128382] pwc: Logitech QuickCam Orbit/Sphere USB webcam detected.
[ 4976.128468] pwc: Registered as /dev/video1.
[ 4976.646430] input: PWC snapshot button as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/input/input15


lsmod | grep pwc:
> 
pwc                    81632  1 
videodev               36736  3 pwc,uvcvideo


I've tried with cheese, camorama, amsn, gst-launch and wxcam, when trying to connect to the camera, its red led gets turned on but no image can be retrieved from it.

Hope someone can help me with this.

---

### Post by GeoMX on 2010-05-01
I've just installed Lucid Lynx and I'm happy to say the camera works again :).

The only problem is that it must be plugged after the system has been started, if not, programs can not retrieve images from it :confused:. Anyway, I'm happy it works because now I can continue with my work :).

---

