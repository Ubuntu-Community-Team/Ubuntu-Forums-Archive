---
title: "rj45 extender and webcam not working"
date: 2013-03-03
forum: Hardware
---

### Post by redactech on 2013-03-03
I want to use a webcam with an rj45 extender (like this one [http://dx.com/p/usb-cable-via-rj45-extender-set-power-boost-up-to-150-feet-6640](http://dx.com/p/usb-cable-via-rj45-extender-set-power-boost-up-to-150-feet-6640)) I've tried the keyboard, printer and mouse, so far so good. But when it comes to the web cam I have the following error in syslog

uvcvideo: Failed to submit URB 0 (-28).


(the webcam works pretty much but I don't have another one to test it )

I've googled the error but with no luck (according to the specific case) does anyone have met this error with a rj45 extender ?

---

### Post by redactech on 2013-03-03
so I keep trying to find what the error message means.

Firing up cheese with the webcam rigged on the rj45 extender (and a cable - btw I tried cat5 and cat6 and various length always the same issue) 

and one error message caught my eye

```
libv4l2: error turning on stream: no space left on device
```



searching the error giving me many people trying to work out many webcam  (which is not my case) but it might be an issue of bandwidth of the usb port

---

