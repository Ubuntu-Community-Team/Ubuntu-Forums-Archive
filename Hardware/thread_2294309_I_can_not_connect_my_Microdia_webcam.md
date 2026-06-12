---
title: "I can not connect my Microdia webcam"
date: 2015-09-10
forum: Hardware
---

### Post by nacc2 on 2015-09-10
Hi,

I have installed an Ubuntu 15.04 64-bits on a Acer ASPIRE 1810TZ. 
And the webcam (inside the laptop) doesn't work with VLC, Cheese, etc...

I've done **lsusb** and this is the result:

Bus 002 Device 002: ID 0c45:6310 Microdia Sonix USB 2.0 Camera
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I also have tried with:
> sudo rmmod uvcvideo
> sudo modprobe uvcvideo

But it still doesn't work.

Anyone can help me?

Thank you very much.

---

