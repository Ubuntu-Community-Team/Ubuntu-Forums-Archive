---
title: "lenovo t500 wi-fi ubuntu 12.04"
date: 2012-05-05
forum: Hardware
---

### Post by bludugululu on 2012-05-05
While upgrading up to 12.04 a problem with wireless connection appeared: ubuntu can find wireless connections, can establish connection, but when any request sending to any server — there is no result.

LAN is working good. Wi-fi is working good with two other computers in the room.

I've tried:

```
$ sudo apt-get update
$ sudo apt-get install firmware-b43-installer
$ sudo apt-get remove bcmwl-kernel-source
$ sudo reboot
```

The respond was: there is no bcmwl-kernel-source package. I've got an advice, that this package should be installed, but it's installation gave nothing.

Step back to 11.10?

---

