---
title: "Ubuntu 20.04 suddenly cannot detect integrated webcam on Lenovo X1"
date: 2022-01-25
forum: Hardware
---

### Post by solveignaess on 2022-01-25
Hi!


I'm new to Ubuntu, and I have Ubuntu 20.04.3 installed on a Lenovo ThinkPad X1 Carbon Gen 9.

In the middle of a zoom call (while at the same time installing Apache Spark), my integrated camera stopped working.
It doesn't work with Cheese either (no device found), and the following command
```

v4l2-ctl --list-devices

```
returns
```

Cannot open device /dev/video0, exiting.

```

The output of 
```
lsusb
```
is
```
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hubBus 003 Device 002: ID 06cb:00fc Synaptics, Inc. 
Bus 003 Device 003: ID 8087:0026 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I tried disabling/enabling the camera in the BIOS, Security, I/O Ports settings. I also tried reinstalling Ubuntu 20.04, but it still doesn't work.

I would be very happy if you have any advice on how to proceed! Please let me know if I should provide any other info.


Best,
Solveig

---

