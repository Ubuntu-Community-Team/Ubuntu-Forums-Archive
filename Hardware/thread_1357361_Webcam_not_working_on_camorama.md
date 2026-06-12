---
title: "Webcam not working on camorama"
date: 2009-12-17
forum: Hardware
---

### Post by sun4help on 2009-12-17
Hi,

Please find below the output of lsusb .

Bus 002 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

but still i am not getting webcam on camorama, its giving cannot connect video device ( /dev/video0)

ls -l /dev/video0 
crw-rw----+ 1 root video 81, 0 2009-12-17 13:12 /dev/video0

please help me 

thanks in advance

---

### Post by PatrickVogeli on 2009-12-17
use cheese, forget about camorama. I believe camorama is deprecated, since it only supports V4L1 devices, while nowdays pretty much all webcam drivers are V4L2 (Video For Linux 1 or 2).

Does it work with cheese?

---

### Post by sun4help on 2009-12-17
thanks ,its works fine ..

---

