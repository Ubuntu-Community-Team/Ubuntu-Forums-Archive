---
title: "Where does my USB camera mount?"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by TeeAhr1 on 2006-12-18
I'm having trouble pulling an avi file off my Canon A430 camera.  There are three files, I select them when the dialog pops up per usual, the first two transfer fine, then it hangs on the third one and I end up having to force quit.

My question, then, is: Where does that camera mount?  Can I manually pull the files off?

---

### Post by antonr on 2008-03-12
I also had trouble getting .AVI files off my Canon IXUS 860 IS.
In my first test, I used konqueror to cut and paste two JPEGs and two AVIs.
The two jpegs made it but the two AVIs arrived with 0 byte length. It looks like the "cut" operation believed that the AVIs made it intact, so the AVIs were deleted from the camera.

But to find the device path, this is what I did.
(There are probably better methods, but this seems to work for me.)

In a console, try: ```
lsusb
``` to list currently attached usb devices.
For my Canon IXUS 860 IS it prints:

```
Bus 003 Device 002: ID 04a9:3160 Canon, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
```

Then you can look in /dev/bus/usb/ for the bus and device.
So for me it was /dev/bus/usb/003/002

Hope that helps.

---

