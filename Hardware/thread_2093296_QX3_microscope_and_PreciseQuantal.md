---
title: "QX3 microscope and Precise/Quantal"
date: 2012-12-10
forum: Hardware
---

### Post by p-dh on 2012-12-10
Hi All,
I have an old Intel QX3 microscope - it still works and is a great tool. I plugged it in (USB), and it was immediately recognized. I could even use Cheese with it. The only problem that I had was in trying to turn on the lights (top and bottom). 
I finally found the solution. Install the package v4l2ucp. If you have a video camera already running, you will probably need to choose File-->Open and choose the last available video device (on my machine, it was /dev/video1). Click on Illuminator 1 for the bottom light and Illuminator 2 for the top. You can also control it through the terminal with v4l2-ctl.
Have fun.

Paul :cool:

---

