---
title: "Logitech ClickSmart 310 webcam"
date: 2006-09-23
forum: Hardware &amp; Laptops
---

### Post by stevesmith on 2006-09-23
Forgive the vagueness of this post, it's not my computer and I'm not in front of it!  My friend's got a Logitech camera, it doesn't work in dapper, in neither amsn nor kopete.

/dev/video and /dev/video0 exist.

Here's lsusb:
```

Bus 002 Device 002: ID 046d:0900 Logitech, Inc. ClickSmart 310
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

From dmesg:
```

[17179706.920000] drivers/usb/media/spca5xx/spca5xx-main.c:
USB SPCA5XX camera found. Logitech ClickSmart 310 (SPCA551+ Agilent HDCS1020)

```

We can't get any joy from troubleshooting in [https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx).

So anyone got the faintest clue why it doesn't work?

---

