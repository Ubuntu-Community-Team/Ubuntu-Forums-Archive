---
title: "Asus F5SL (or X50SL :S) Integrated WebCam Problems"
date: 2009-03-29
forum: Hardware
---

### Post by J-E-N-O-V-A on 2009-03-29
I'm having some difficulty getting my integrated webcam working on my Asus Laptop with Ubuntu 8.10

When I run "lsusb", I get:

Bus 003 Device 003: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 003 Device 002: ID 04f2:b033 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

When I run lsmod | grep videodev, I get:

videodev               41344  1 uvcvideo
v4l1_compat            22404  2 uvcvideo,videodev

I haven't really tried anything and haven't found anything online to help. I don't know where to start!

---

### Post by J-E-N-O-V-A on 2009-03-29
```
sudo apt-get install cheese
```
```
cheese
```
Resolved, lol. Apologies for the pointless thread.

---

### Post by j_arquimbau on 2009-10-20
I've got the same computer and the cam works upside-down... Could you manage to solve this?
Thank you.

---

