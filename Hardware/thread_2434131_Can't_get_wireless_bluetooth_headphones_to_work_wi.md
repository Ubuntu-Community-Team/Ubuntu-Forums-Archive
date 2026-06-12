---
title: "Can't get wireless bluetooth headphones to work with Ubuntu on a Macbook Pro"
date: 2019-12-31
forum: Hardware
---

### Post by ttofit on 2019-12-31
Hi, 

I am unable to get my Lindy BNX-60 bluetooth headphones working with my Macbook Pro 15", Core i7, Mid-2015 running Ubuntu 18.04. 

I can connect to them but sound cuts in and out and sometimes disappears altogether. 

Output of  > lspci -knn | grep Net -A3; lsusb

> 03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM43602 802.11ac Wireless LAN SoC [14e4:43ba] (rev 01)
    Subsystem: Apple Inc. BCM43602 802.11ac Wireless LAN SoC [106b:0133]
    Kernel driver in use: brcmfmac
    Kernel modules: brcmfmac
Bus 002 Device 002: ID 05ac:8406 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 05ac:8290 Apple, Inc. 
Bus 001 Device 003: ID 05ac:0274 Apple, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

What can I do to fix this issue?

Thanks.

---

