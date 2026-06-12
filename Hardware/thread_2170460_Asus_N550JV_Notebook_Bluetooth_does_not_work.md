---
title: "Asus N550JV Notebook: Bluetooth does not work"
date: 2013-08-26
forum: Hardware
---

### Post by sgehlich on 2013-08-26
Hey,

I just installed a fresh copy of Ubuntu 13.04 on my new Asus N550JV Notebook, but I couldn't get Bluetooth to work. Bluetooth appeared to be active, but there was no option to add a new device.

I found out that the device id of my Bluetooth device is 13d3:3402, so I looked at the kernel source code and found out that the support for my device has been added during the 3.11-rc7 development:

[https://github.com/torvalds/linux/commit/5b77a1f3d7b7360dc2b7c6d2188d39b9f8432907](https://github.com/torvalds/linux/commit/5b77a1f3d7b7360dc2b7c6d2188d39b9f8432907)

So I installed 3.11-rc7 and after a few reboots, I could finally get it to pair with my bluetooth keyboard. After the next restart, the option to add a new device was gone again. After restarting a couple of times, it worked again. A very weird behaviour.

Can somebody help me?

---

