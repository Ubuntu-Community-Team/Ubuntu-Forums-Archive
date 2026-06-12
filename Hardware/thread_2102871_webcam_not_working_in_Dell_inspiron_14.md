---
title: "webcam not working in Dell inspiron 14"
date: 2013-01-08
forum: Hardware
---

### Post by mailfromsaurabh on 2013-01-08
Hi
I have integrated webcam and it is not working. I tried cheese , camorama and xawtv and cheese says "No device found"

Below are few details I have collected-

saurabh@saurabh-Dell-System-Inspiron-N4110 ~ $ xawtv
This is xawtv-3.102, running on Linux/x86_64 (3.2.0-23-generic)
xinerama 0: 1366x768+0+0
vid-open-auto: failed to open a capture device
vid-open: could not find a suitable videodev
no video grabber device available

saurabh@saurabh-Dell-System-Inspiron-N4110 ~ $ lsmod|grep videodev
videodev 98259 1 uvcvideo
v4l2_compat_ioctl32 17128 1 videodev
saurabh@saurabh-Dell-System-Inspiron-N4110 ~ $ lsmod|grep uvcvideo
uvcvideo 72627 0
videodev 98259 1 uvcvideo

saurabh@saurabh-Dell-System-Inspiron-N4110 ~ $ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 004: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth

If anyone knows about fix, let me know

---

### Post by mailfromsaurabh on 2013-01-08
> **mailfromsaurabh said:**
> Hi
I have integrated webcam and it is not working. I tried cheese , camorama and xawtv and cheese says "No device found"

Below are few details I have collected-

saurabh@saurabh-Dell-System-Inspiron-N4110 ~ $ xawtv
This is xawtv-3.102, running on Linux/x86_64 (3.2.0-23-generic)
xinerama 0: 1366x768+0+0
vid-open-auto: failed to open a capture device
vid-open: could not find a suitable videodev
no video grabber device available

saurabh@saurabh-Dell-System-Inspiron-N4110 ~ $ lsmod|grep videodev
videodev 98259 1 uvcvideo
v4l2_compat_ioctl32 17128 1 videodev
saurabh@saurabh-Dell-System-Inspiron-N4110 ~ $ lsmod|grep uvcvideo
uvcvideo 72627 0
videodev 98259 1 uvcvideo

saurabh@saurabh-Dell-System-Inspiron-N4110 ~ $ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 004: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth

If anyone knows about fix, let me know

Correction I have Dell Inspiron N4110 in specific.

---

