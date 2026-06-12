---
title: "dots/lines on my screen"
date: 2010-07-26
forum: Hardware
---

### Post by akalyptos on 2010-07-26
I have  Fujitsu Siemens and I just installed Ubuntu 10.04 LTS and i have some dots/lines on my screen posibly due to refresh rate. I am a new user of Ubuntu

---

### Post by dino99 on 2010-07-26
check that the driver is activated: system admin hardware driver

---

### Post by akalyptos on 2010-07-26
-----------------------------------------
The SmartLink modem daemon is the application part of thedriver for recent modems produced by Smart Link Ltd.

This package replaces (along with hardware access drivers) the olddriver generation (2.7.x) which consisted of kernel modules only.

It needs a kernel driver to access the hardware. This can be eitherrecent ALSA (shipped with a newer kernel (>=2.6.4) with ALSA supportand snd-intel8x0m module) which is sufficient for basic operation anddata/Internet connection, or the SmartLink kernel driver which isprovided by separate packages which you can build using the source fromthe sl-modem-source package.

This driver enables the usage of many software modems, as commonly found in laptops.

If this driver is not enabled, you will not be able to use your modem.
-------------------------------------------------

This is what appeared. I dont know if it is activated

---

