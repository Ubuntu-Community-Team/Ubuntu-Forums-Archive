---
title: "Compaq C700 - Webcam gives grainy incorrect output"
date: 2009-01-22
forum: Hardware
---

### Post by ashkool on 2009-01-22
Hi All, this is my first post to the community. Glad to be here.

I switched to linux a month back, and from Fedora to Ubuntu around two weeks back. The distro is simply great and the ubuntu forums helped me a great deal in configuring my system and getting all the help i needed to move from windows to linux.

The only problem remaining is about my webcam on my Compaq C771TU notebook.
lsusb output:
$ lsusb
Bus 004 Device 004: ID 064e:c108 Suyin Corp. 
Bus 004 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Cheese detects my webcam, but it's all grainy and colors are incorrect. I'm attaching a screenshot. A bit of searching lead me to 
[https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/282473](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/282473)
Even after installing the latest version of libv4l (0.5.8-1), I still can't get the right output. And I couldn't get lib32v4l-0 as said in the above launchpad link. How can i solve this?

Thanks in advance for your time.

---

