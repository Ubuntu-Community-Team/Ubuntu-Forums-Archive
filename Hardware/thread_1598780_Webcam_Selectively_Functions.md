---
title: "Webcam Selectively Functions"
date: 2010-10-17
forum: Hardware
---

### Post by Nate_the_Ace on 2010-10-17
Hello again everyone,

   I am here with a head-scratcher of a problem. I am still having problems with this very standard USB 2.0 webcam of mine. Every time I try to use an application like Cheese, it causes a kernel panic.

   I have discovered something interesting, VLC is able to stream the video feed just fine. It's in the device list, and I click on it, and the little light comes on and there is my face.

   I think it may have to do with improper permissions, or it could be a problem with the UVC driver. Does VLC use UVC to communicate with the webcam? If so, then why does it not work with Cheese?

   Thanks in advanced,
Nate

*lsusb terminal output*

```
nathan@Nathan-Laptop:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b027 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

