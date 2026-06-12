---
title: "xawtv and multimedia capture card"
date: 2011-03-15
forum: Hardware
---

### Post by kios on 2011-03-15
Hy. I'm trying to setup a surveillance system on a ubuntu 10.04 server. I have a Techwell tw6802 pci capture card that show up when using lspci

```

03:01.0 Multimedia video controller: Techwell Inc. TW6802 multimedia video card (rev 10)
03:01.1 Multimedia controller: Techwell Inc. TW6802 multimedia other device (rev 10)

```

I have installed xawtv but when i run it it says there is no video device.

```

This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.32-28-server)
xinerama 0: 1024x768+0+0
can't open /dev/video0: No such device or address
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such device or address
v4l2: open /dev/video0: No such device or address
v4l: open /dev/video0: No such device or address
no video grabber device available

```

Can anyone give any suggestions? Also tried xawtv -hwscan but it only returns the Intel video card and "no such device or address" for video0/1/2/3

Thanks

---

