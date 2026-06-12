---
title: "Web Cam"
date: 2010-03-17
forum: Hardware
---

### Post by mary.ydm on 2010-03-17
Hi after checking that I would be able to use a Logitech Webcam C200 on Linux I bought one but my computer does not even see it! How can I get this installed and working?  Im using 9.10 Karmic.

---

### Post by silencej on 2010-03-17
> **mary.ydm said:**
> Hi after checking that I would be able to use a Logitech Webcam C200 on Linux I bought one but my computer does not even see it! How can I get this installed and working?  Im using 9.10 Karmic.

You could try Guvcview by:
```
sudo apt-get install guvcview
```

UVC stands for "usb video class".
So i guess when you install guvcview, it will automatically install the demanded libraries for you, e.g. libwebcam.

---

### Post by JolietJake88 on 2010-09-02
sorry..but i have the same problem with ubuntu 10.04...with logitech c200..i'm going crazy!!! can someone help me?:confused:

---

