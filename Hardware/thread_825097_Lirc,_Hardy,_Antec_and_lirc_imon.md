---
title: "Lirc, Hardy, Antec and lirc_imon"
date: 2008-06-10
forum: Hardware
---

### Post by mandyfester on 2008-06-10
Hello

I am having problems getting my hauppauge pvr150 receiver working. After a fresh install of Hardy everything works nicely (tried this numerous times).  After a reboot my hauppauge receiver is as useful as a brick.

I think I have traced the problem to a conflict to my Antec case. Lirc apparently loads lirc_imon which then screws everything up. I have a lirc0 and lirc1 in /dev/lirc

I have tried adding 
options lirc_imon islcd=0

to /etc/modprobe.d/options

Lirc only starts one device, lirc0, but still no joy. dmesg says that islcd is an unknown parameter.

I have also tried to blacklist lirc_imon but still nothing.

Using mode2 and starting lircd manually also give me nothing.

My dmesg output is as follows:

```
[   33.723230] lirc_dev: IR Remote Control driver registered, at major 61 
[   33.759062] lirc_pvr150: chip found with RX and TX
[   33.760133] lirc_dev: lirc_register_plugin: sample_rate: 0
[   33.932104] lirc_pvr150: firmware of size 302355 loaded
[   33.932377] lirc_pvr150: 743 codesets loaded
[   33.970089] lirc_pvr150: Hauppauge PVR-150 IR blaster: firmware version 1.3.0
[   34.189136]  [<ffffffff88c8a9ef>] :lirc_i2c:init_module+0x4f/0x60
[   34.189163]  [<ffffffff88c7e0d0>] :lirc_dev:lirc_register_plugin+0x0/0x520
[   34.189219]  [<ffffffff88c8a9ef>] :lirc_i2c:init_module+0x4f/0x60
[   34.189243]  [<ffffffff88c7e0d0>] :lirc_dev:lirc_register_plugin+0x0/0x520

```
Please can someone help me before I install Microsoft Media Center?

Thanks

Andy

---

