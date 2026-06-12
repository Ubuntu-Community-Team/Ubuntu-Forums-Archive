---
title: "Using two Logitech C910 HD webcams"
date: 2011-01-07
forum: Hardware
---

### Post by jonim8or on 2011-01-07
I'm trying to use two Logitech C910 HD webcams on my laptop. When I plug them in two usb ports on the same bus, they won't run at the same time. guvcview crashes with:
```

libv4l2: error turning on stream: Device or resource busy
VIDIOC_STREAMON - Unable to start capture: Device or resource busy

```

Now my laptop is not so rich in USB ports (3 usb ports on Bus 002 and 1 USB 3.0 port on Bus 003). So I tried plugging one of the webcams in the USB3.0 port, but it isn't even detected (it does not show up in lsusb, nor in guvcview).

So now I have several possible solutions:
1) use an usb3.0 hub, see if that works (like in [this post](http://ubuntuforums.org/showthread.php?p=10327382#post10327382))
2) Do something to make the usb 3.0 port recognize my webcam (but I don't know how)

As the other thread already handles the first option, my question here is: how can I make my usb 3.0 port recognize my webcam?

---

