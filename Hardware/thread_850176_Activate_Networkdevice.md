---
title: "Activate Networkdevice"
date: 2008-07-05
forum: Hardware
---

### Post by -Seba- on 2008-07-05
Hi!

I just wanted to ask how I activate a hardware-device inside the terminal or via the xubuntu-surface. The exact story of my problem is here:

------

I just installed Xubuntu on an acer Extensa 5220; everything looks fine except the w-lan-device. It's a Broadcom something, and what I've done so far is, according to some tutorials ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)), installed the ndiswrapper and installed the driver for that Broadcom card (id 14e4:4311).

So if I type now "ndiswrapper -l" in the terminal, it answers "bcmwl5: driver installed | device (14E4:4311) present (alternate driver: bcm43xx)". Since I've already blacklisted all other native drivers for the network card, I suppose everything should be fine with the drivers.

I guess what still doesn't work is the fact, that after I type "lshw" in the terminal, it sais "*-network DISABLED"

------

So my question is, how can I activate the network card inside the terminal or via the Xubuntu-surface? I suppose that this is a rather simple question, but believe it or not, I've been googling around all night and haven't found anything helpful...

Thanks a lot
Sebastian

---

