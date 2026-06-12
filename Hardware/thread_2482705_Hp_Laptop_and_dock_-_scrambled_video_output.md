---
title: "Hp Laptop and dock - scrambled video output"
date: 2023-01-08
forum: Hardware
---

### Post by owenpeterson on 2023-01-08
Hello! I just installed Ubuntu 22.04 onto an HP Elitebook 840 G5 laptop. Everything is good with the laptop, but when I'm connected to the HP Ultraslim docking station (which has two Display Port outputs) the video output is scrambled to my two monitors. Both monitors are 27" 2560x1440 MSI monitors. Ubuntu correctly detects that I have two 2560x1440 monitors connected. 

Here is the docking station I'm using:
[https://support.hp.com/us-en/product/hp-2013-ultraslim-docking-station/5450893/document/c03958207](https://support.hp.com/us-en/product/hp-2013-ultraslim-docking-station/5450893/document/c03958207)

Has anyone encountered this issue with HP docking stations and resolved it? I have a feeling it's due to the higher resolution of the monitors, but since it's not a USB-C connection I'm hoping it can sorted out.

So far all I've tried is this driver, which didn't resolve the problem (it's probably for USB-C connections?). 
[https://www.synaptics.com/products/displaylink-graphics/downloads/ubuntu](https://www.synaptics.com/products/displaylink-graphics/downloads/ubuntu)

Here's a link to the output from the system-info script:
[https://paste.ubuntu.com/p/RrrrdDP28h/]("https://paste.ubuntu.com/p/RgbKdQXmNN/")


Thanks!

---

### Post by owenpeterson on 2023-01-08
Update: I got the video output working correctly using some DisplayPort to HDMI adapters with HDMI cables. Previously I was using a DisplayPort to HDMI cable (that only supported 1920x1080 according to the specs for it) so if anyone has experience with good quality DisplayPort to HDMI cables (so I can omit the adapters)  that work with 2560x1440 please let me know. Thanks!

---

