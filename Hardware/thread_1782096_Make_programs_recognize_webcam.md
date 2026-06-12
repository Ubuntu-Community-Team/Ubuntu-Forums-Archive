---
title: "Make programs recognize webcam"
date: 2011-06-14
forum: Hardware
---

### Post by mathprodigy20 on 2011-06-14
I just bought a new Logitech Webcam Pro 9000 to use with some computer vision software I'm working with. I'm running Ubuntu 11.04 (natty), and I can't get the camera to work with anything on my computer. It's recognized by the system (i.e. shows up when I do a lsusb), but neither cheese nor OpenCV (the software I'm attempting to use) recognize a camera plugged in. Any ideas why these applications can't see the camera?

---

### Post by mathprodigy20 on 2011-06-15
I figured it out. For some reason I didn't have permission as a normal user to access the camera. No problem when I tried it as a superuser.

---

