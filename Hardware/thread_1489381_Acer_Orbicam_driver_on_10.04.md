---
title: "Acer Orbicam driver on 10.04"
date: 2010-05-21
forum: Hardware
---

### Post by PyroJing on 2010-05-21
I'm having a problem getting my Acer Orbicam to work with Ubutnu 10.04. I've tried Camorama and Cheese, and it can't detect the camera, which is built into the laptop, and there is no video0, how can I fix this? I am a newb to Linux btw.

---

### Post by PyroJing on 2010-05-21
Here is my lsusb readout

pyrojing@ubuntu:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:0892 Logitech, Inc. OrbiCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by st0nes on 2010-06-25
I can't get mine to work either.  Here's my lsusb:

mark@addy-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 5986:0200 Acer, Inc OrbiCam
Bus 001 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by kelvin spratt on 2010-06-25
My wife can't get orbit cam to work in windows so what chance has it in Linux.

---

