---
title: "VGP-VCC8 Camera"
date: 2010-10-15
forum: Hardware
---

### Post by weaselnet on 2010-10-15
Using a Sony VGN-FZ290 notebook and the camera shows up when I do a lsusb.

Bus 007 Device 005: ID 044e:3012 Alps Electric Co., Ltd 
Bus 007 Device 004: ID 044e:3013 Alps Electric Co., Ltd 
Bus 007 Device 003: ID 044e:3010 Alps Electric Co., Ltd Bluetooth Adapter
Bus 007 Device 002: ID 044e:3011 Alps Electric Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:183b Ricoh Co., Ltd Visual Communication Camera VGP-VCC8 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

However I get a uvcvideo fail at boot and Cheese does not recognize a valid device. 

Any suggestions?

Worked fine at the start with 10.04.

---

### Post by weaselnet on 2010-10-21
These steps resolved my issue.

1. sudo add-apt-repository ppa:r5u87x-loader/ppa
2. sudo apt-get update
3. sudo apt-get install r5u87x
4. sudo /usr/share/r5u87x/r5u87x-download-firmware.sh

---

### Post by 00arthuryu on 2010-11-28
Thanks :D
Worked perfectly on 10.10 AMD64 VGN-CR42S/W

---

### Post by jvan_ca on 2011-01-02
I have tried this formula for my webcam, and everything worked, however once I rebooted, Skype went all fuzzy and cheese put me upsidedown.

Here is my lsusb:

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ca:1837 Ricoh Co., Ltd Visual Communication Camera VGP-VCC4 [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I've installed UVC video driver and libv4l driver and now the driver in this forum.

I'm not sure what steps to follow now.

---

