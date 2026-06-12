---
title: "How to zoom in and out with a webcam"
date: 2020-07-30
forum: Hardware
---

### Post by Yahoé on 2020-07-30
I am using a Logitech C930E webcam on Ubuntu 20.04. How can use the webcam’s zooming feature? Can I invoke this zooming feature in Cheese, Zoom, etc.?

---

### Post by TheFu on 2020-07-30
```
v4l2-ctl -d /dev/video0 -c zoom_absolute=200
```

This assumes the Video-4-Linux v2 device is /dev/video0.
Works on a Logitech C920 Pro.

---

