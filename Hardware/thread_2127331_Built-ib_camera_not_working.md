---
title: "Built-ib camera not working"
date: 2013-03-19
forum: Hardware
---

### Post by nahumaharon on 2013-03-19
I am running Ubuntu 12.04LTS on my Lenovo G570

I can't make built-in camera working - no program I am using can't recognize it... Cheese, Skype, etc.
The camera is working fine under Windows 


lsusb output :

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 04f2:b272 Chicony Electronics Co., Ltd Lenovo EasyCamera






Googled it, looked in this forums, still can't sove the problem .
On Lenovo site found only Win drivers...

anybody ??????

---

### Post by bcschmerker on 2013-03-19
As of 19 March 2013, the [LinUX USB Video Class Project]("http://www.ideasonboard.org/uvc/") has no working driver for the newest Chicony® cameras in Lenovo® portable computers; the latest suported CCD chip is the Integrated Camera (Lenovo® ThinkPad® T420s notebooks), which predates your [ThinkPad® G570]("http://www.lenovo.com/products/us/tech-specs/laptop/essential/g-series/g570/").

---

### Post by nahumaharon on 2013-03-20
> **bcschmerker said:**
> As of 19 March 2013, the [LinUX USB Video Class Project]("http://www.ideasonboard.org/uvc/") has no working driver for the newest Chicony® cameras in Lenovo® portable computers; the latest suported CCD chip is the Integrated Camera (Lenovo® ThinkPad® T420s notebooks), which predates your [ThinkPad® G570]("http://www.lenovo.com/products/us/tech-specs/laptop/essential/g-series/g570/").



Ouch... does it mean I have to install Windows to use my camera or there is some way to make it working anyway ?

---

