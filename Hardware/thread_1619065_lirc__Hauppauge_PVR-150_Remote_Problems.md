---
title: "lirc / Hauppauge PVR-150 Remote Problems"
date: 2010-11-11
forum: Hardware
---

### Post by Steviebe on 2010-11-11
I'm having trouble getting my PVR-150 Remote to work with lirc.  It was working yesterday with Ubuntu 9.10, but I did a fresh install last night with Lubuntu 10.10.

I have installed lirc, but I get no output to irw.

If anyone can help me out, I would be grateful.  I'll try to list relevant information, but let me know if I missed something.

[INDENT]$ dmesg |grep lirc
[   14.111699] lirc_dev: IR Remote Control driver registered, major 249 
[   14.339501] lirc_i2c: module is from the staging directory, the quality is unknown, you have been warned.

$ lsmod |grep lirc
lirc_i2c                5825  0 
lirc_dev                9393  1 lirc_i2c[/INDENT]

My device is not listed in /proc/bus/input/devices, so I'm thinking that's the right place to start, but to be honest, I'm not sure what to do.

---

