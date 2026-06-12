---
title: "Enable USB Hotplug for USB-LAN device?"
date: 2012-02-14
forum: Hardware
---

### Post by yogithite on 2012-02-14
Hi,

Yesterday I installed Ubuntu 11.10 image on my laptop. I am trying to  enable USB hotplug for one of my USB data cards. Instructions from  vendor were:

1. Edit the file /etc/modprobe.conf 
2. Add an entry for usbx - line: alias usbx usblan
3. File ifcfg-usbx has been added under /etc/sysconfig/network-scripts
4. Load LAN module

With this 11.10 image, I dont see /etc/modprobe.conf and /etc/sysconfig/network-scripts :confused: . 

I can see directory: /etc/modprobe.d. I tried to add usblan.conf over  there with the mentioned alias but I am not sure if I am following right  steps. Need help :sad:

Please provide inputs with which I can convert above steps to be compatible with 11.10 image!

Yogi

---

