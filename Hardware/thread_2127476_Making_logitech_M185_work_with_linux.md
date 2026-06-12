---
title: "Making logitech M185 work with linux"
date: 2013-03-20
forum: Hardware
---

### Post by Cyril4133 on 2013-03-20
Since Logitech doesn't provide any linux driver for their wireless mouse, I was wondering whether someone had found some way to make it work on linux.

There is some chance since it is detected by lsusb:

> lsusbBus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 147e:2020 Upek 
Bus 001 Device 004: ID 0a5c:21e6 Broadcom Corp. 
Bus 001 Device 005: ID 04f2:b2da Chicony Electronics Co., Ltd 


lomoco says

> lomoco -s004.001: 1d6b:0003 Not a Logitech device
003.002: 046d:c52f Unsupported Logitech device: Unknown
003.001: 1d6b:0002 Not a Logitech device
002.002: 8087:0024 Not a Logitech device
002.001: 1d6b:0002 Not a Logitech device
001.005: 04f2:b2da Not a Logitech device
001.004: 0a5c:21e6 Not a Logitech device
001.003: 147e:2020 Not a Logitech device
001.002: 8087:0024 Not a Logitech device
001.001: 1d6b:0002 Not a Logitech device





Thank you,

---

### Post by Cyril4133 on 2013-03-20
I have tested the mouse with xubuntu live and it worked perfectly but I cannot figure out the difference with my system. 

Thanks

---

