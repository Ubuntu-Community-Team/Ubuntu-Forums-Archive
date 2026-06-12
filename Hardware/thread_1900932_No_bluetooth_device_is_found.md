---
title: "No bluetooth device is found"
date: 2011-12-27
forum: Hardware
---

### Post by jjleonb on 2011-12-27
Hi, I've been using ubuntu the last 2 years, in my laptop and in my desktops, but since I've been using ubuntu in my laptop the bluetooth is not working, now i'm using ubuntu 11.10, and everything is working well, excepting the bluetooth.  These are the commands that I made and these are the results:

root@tux3-laptop:/home/tux3# hcitool -i dev
Invalid device: No such device
root@tux3-laptop:/home/tux3# 

root@tux3-laptop:/home/tux3# hcitool scan
Device is not available: No such device
root@tux3-laptop:/home/tux3# 

root@tux3-laptop:/home/tux3# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 003 Device 008: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 005 Device 002: ID 04fc:05da Sunplus Technology Co., Ltd 
Bus 003 Device 009: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 003 Device 010: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
root@tux3-laptop:/home/tux3# 

By the way, I have a utility on my desktop that manages the bluetooth but it says Bluetooth is disabled, I configured the bios to use the switch for my wireless card and bluetooth but unfortunately it seems it's not working. The wireless connection is working fine.

Any advice will be welcome.  Thanks in advance.

---

