---
title: "Quickcam Express not runing"
date: 2009-01-25
forum: Hardware
---

### Post by Kraut~salat on 2009-01-25
hi, I'm trying to get my Logitech Quickcam Express running with my fearless mountain goat (i.e. intrepid ibex 8.10).
I can see it:
> tim@algebra:~$ lsusb -s 002:007
Bus 002 Device 007: ID 046d:0920 Logitech, Inc. QuickCam Express

and the modules get loaded:
> tim@algebra:/lib/modules/2.6.27-8-eeepc/kernel/drivers$ lsmod|grep gspca
gspca_tv8532           12544  0
gspca_main             21376  1 gspca_tv8532
videodev               33408  2 gspca_main,uvcvideo
usbcore               141552  9 gspca_tv8532,gspca_main,uvcvideo,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd

According to the gspca website (mxhaard.free.fr) the tv_8532 is the right one for my cam and it's supposed to be supported. I also get a new video device /dev/video1.

But when I try to use it it doesn't work:> 
tim@algebra:~$ gst-launch -v v4l2src device=/dev/video1 ! xvimagesink
Setting pipeline to PAUSED ...
/GstPipeline:pipeline0/GstV4l2Src:v4l2src0.GstPad:src: caps = video/x-raw-yuv, format=(fourcc)YV12, width=(int)352, height=(int)288, framerate=(fraction)100/1
Pipeline is live and does not need PREROLL ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock
libv4l2: error dequeuing buf: Input/output error
libv4l2: error dequeuing buf: Input/output error
^Vlibv4l2: error dequeuing buf: Input/output error
^C^CCaught interrupt -- handling interrupt.
Interrupt: Stopping pipeline ...
Execution ended after 10670155634 ns.
Setting pipeline to PAUSED ...
libv4l2: error dequeuing buf: Input/output error
^C

The input/output error keeps repeating, so I Ctrl+C killed it. Check the framerate:100. That's not right. Seems like the capabilities of the device are queried incorrectly.
Kopete just gets stuck trying to use the cam and camorama just complains it cannot connect to the video device.

Please help me. I think I did everything right,  just the driver doesn't work properly. My system:
> tim@algebra:~$ uname -s -r
Linux 2.6.27-8-eeepc
Ubuntu 8.10. As you can see it's a Asus eeePC, but I have the same problem on my other laptop, regular 32bit kernel, version 2.6.27-9.

cheers, Kraut (aka Tim as you might have guessed by now)

---

