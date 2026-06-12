---
title: "HELP ME!! Can't configurate Intel GMA X3100 video memory in Ubuntu 8.1"
date: 2009-04-15
forum: Hardware
---

### Post by yurichang on 2009-04-15
Hi everybody,

I have a problem trying to configure my graphic card of my laptop (Toshiba Satellite A305-S6829), I have installed Ubuntu 8.1. 

I've tried to change my XORG.CONF, but i'm not sure what I have to change exactly, this is what I have.

     Section "Device"
             Identifier "Configured Video Device"
     EndSection
     Section "Monitor"
             Identifier "Configured Monitor"
     EndSection
     Section "Screen"
             Identifier "Default Screen"
             Monitor "Configured Monitor"
             Device "Configured Video Device"
     EndSection


I haven't found the driver for my video card (Intel GMA X3100).
Please help me!!

PD. Sorry for my English

---

