---
title: "No image from camera"
date: 2015-12-27
forum: Hardware
---

### Post by kobras on 2015-12-27
Trying to connect webcam to one old desktop computer. Checking in skype and I can see only black image. So I have tried to use [this]("https://help.ubuntu.com/community/Webcam/Troubleshooting#Picture_is_Dark").

guvcview tool prints to terminal next error messages:

```
V4L2_CORE: Could not grab image (select timeout): Resource temporarily unavailable
```

I have tried to use different parameters (fps, resolution) but there is no effect. I can't even capture images.

Do you have any ideas?

---

### Post by kobras on 2015-12-31
Problem was in broken usb port. In other socket camera works fine.

---

