---
title: "Video camera fails to initialize"
date: 2018-11-25
forum: Hardware
---

### Post by lordbah2 on 2018-11-25
I've just noticed my video camera no longer works. It has worked in years past. I'm not sure whether I've seen it work since the latest upgrade to Ubuntu 18.04.1 and gnome/wayland - maybe not. The camera is built-in on a Dell monitor. The computer is a System 76 leox2 desktop.

```
[254106.805739] uvcvideo: Found UVC 1.00 device Monitor Webcam (05a9:2649)
[254106.806056] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[254106.806431] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[254106.806435] uvcvideo: Failed to initialize the device (-5).
[254106.806474] usbcore: registered new interface driver uvcvideo
[254106.806475] USB Video Class driver (1.1.1)

Bus 001 Device 006: ID 05a9:2649 OmniVision Technologies, Inc.
``` 

I'm assuming the failure to initialize is why /dev/video* isn't being created.

Where can I go from here? Web searches have lead me only to 2009 posts with solutions which haven't helped.

---

