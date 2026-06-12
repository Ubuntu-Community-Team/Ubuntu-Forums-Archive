---
title: "acer aspire 5750G webcam suddenly stopped working"
date: 2011-08-16
forum: Hardware
---

### Post by Mr.Pytagoras on 2011-08-16
hi, I've installed ubuntu 11.04 on my new acer laptop, ubuntu automaticaly detected webcam and it worked out of box with cheese(I didn't try any other app) however after some setting my webcam stopped working.

The actual problem is that after registering new interface it gets deregistered and I don't know how to stop that(on boot)

dmesg | grep uvcvideo:
```
jkalmar@supercomp:~$ dmesg | grep uvcvideo
[    7.596747] uvcvideo: Found UVC 1.00 device 1.3M HD WebCam (058f:b002)
[    7.602003] usbcore: registered new interface driver uvcvideo
[   18.004496] usbcore: deregistering interface driver uvcvideo

```after modprobe uvcvideo it works:
```
jkalmar@supercomp:~$ dmesg | grep uvcvideo
[    7.596747] uvcvideo: Found UVC 1.00 device 1.3M HD WebCam (058f:b002)
[    7.602003] usbcore: registered new interface driver uvcvideo
[   18.004496] usbcore: deregistering interface driver uvcvideo
[ 1612.495239] uvcvideo: Found UVC 1.00 device 1.3M HD WebCam (058f:b002)
[ 1612.499198] usbcore: registered new interface driver uvcvideo
jkalmar@supercomp:~$ 

```what should i do to fix my camera to work without to need to manualy reload the module?

thanks

---

