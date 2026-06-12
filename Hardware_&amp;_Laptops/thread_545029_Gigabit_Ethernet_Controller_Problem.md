---
title: "Gigabit Ethernet Controller Problem"
date: 2007-09-07
forum: Hardware &amp; Laptops
---

### Post by shoaibnawaz on 2007-09-07
I have Acer Veriton 6800 in my office. It has a Marvell Yukon 88E8052 PCI-E ASF Gigabit Ethernet Controller on-board.

The problem is that Ubuntu 7.04 does not support it. However it is working on Win XP on the same system. 

How to check whether the device is detected by Ubuntu?
How to install drivers for it?

Thanks for your precious time to pay attention.

---

### Post by blueturtl on 2007-09-07
You can always check if it appears under System->Network.
If not, open up a terminal and type the command
> lspci

This should give you a list of detected devices.
If you can't find anything that looks like it could be a network adapter you're probably out of luck until the next release. If it's listed you might need to load a driver module for it.

Maybe someone else can help you with locating the proper module and how to load it because I have little experience doing that.

---

### Post by heidfirst on 2007-09-07
Hi,

I have a fujitsu laptop with a Marvell 88E8055 PCI-E Gigabit Ethernet Controller which is supported on ubuntu 6.10 by the sky2 driver.

lspci |grep Mar
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)


lsmod |grep sky
sky2                   43012  0

A google search indicates that this driver supports a number of the Marvell devices, however I cannot find a complete list.

Hope this helps
Gordon

---

### Post by shoaibnawaz on 2007-09-08
Can you please inform me the link to download sky2 drivers for my Marvell Ethernet Controler.

---

