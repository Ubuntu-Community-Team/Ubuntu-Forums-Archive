---
title: "Problem with Inspiron 1525 integrated webcam on Hardy"
date: 2009-05-04
forum: Hardware
---

### Post by caprilo on 2009-05-04
I have an Inspiron 1525n with Ubuntu Hardy preinstalled. At the beginning, the webcam worked fine, but at some point after an update it stopped working. When I open Cheese, the blue light stays on, but no image appears; when I open Camorama, it says "Could not connect to video device (/dev/video0). Please check connection.", and when I open Ekiga, nothing happens.

I've tried the solution in [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Camera_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Camera_Does_Not_Work) , which did not apply since Hardy already comes with v4l2.

I tried to install the Linux backports as it suggests on [http://ubuntuforums.org/showthread.php?t=722870&highlight=1525+webcam](http://ubuntuforums.org/showthread.php?t=722870&highlight=1525+webcam) , but found I have the most recent ones.

I also tried the solution in [http://ubuntuforums.org/archive/index.php/t-793513.html](http://ubuntuforums.org/archive/index.php/t-793513.html), which took me to a more recent version of uvc in [http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/) when compiling. None of them worked, but the dmesg output changed from

[ 20.719793] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:7670)
[ 20.720088] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[ 20.720337] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[ 20.720340] uvcvideo: Failed to initialize the device (-5).
[ 20.720371] usbcore: registered new interface driver uvcvideo

to

[  781.430654] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[  781.431351] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[  781.490208] usbcore: registered new interface driver uvcvideo

and the lsmod is now

uvcvideo               63244  0 
videodev               40224  1 uvcvideo
v4l1_compat            15108  2 uvcvideo,videodev
usbcore               146028  6 uvcvideo,hsfosspec,usbhid,ehci_hcd,uhci_hcd

What can I do?

---

### Post by twent4 on 2009-05-07
I didn't follow all those links, by did you try unloading the module and reloading it? I had a similar issue on Jaunty and it seems to be conflicting with something that loads after uvcvideo does (maybe usbaudio)?

```
sudo modprobe -r uvcvideo
sudo modprobe uvcvideo
```

---

