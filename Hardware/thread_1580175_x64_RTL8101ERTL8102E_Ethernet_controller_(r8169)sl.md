---
title: "x64 RTL8101E/RTL8102E Ethernet controller (r8169)slow speeds"
date: 2010-09-23
forum: Hardware
---

### Post by nirvansk815 on 2010-09-23
Hi all. First let me introduce my laptop:

product: HP Pavilion dv4 Notebook PC
vendor: Hewlett-Packard
OS: Ubuntu 10.04 LTS x64

And the hardware in question:

product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10EC:8136]
vendor: Realtek Semiconductor Co., Ltd. [10EC]
bus info: pci@0000:03:00.0
logical name: eth0
version: 02
Driver:  r8169

The Problem: After purchasing Netgear's [WNDR37AV]("http://www.netgear.com/products/home/wirelessrouters/high-performance/WNDR37AV.aspx") and getting my wireless network all setup I needed to transfer a rather large file from my server to my laptop. I figured "wired" was the way to go. Turns out with a full-duplex 100Mbit connection my notebook was only getting ~30Mbit/s from the server. Server cpu load was low, and it has a 1000Mbit connection so I knew something was wrong. To make a long story short, all I had to do was install the latest drivers from [here]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false"). After following their easy installion procedures I performed the same transfer and was getting ~70Mb/s. Sweeeeeet. Just wanted to pass this info to anyone else who may have similar issues.

Mike

---

### Post by MiThRaZoR on 2011-08-26
Thank you! I've been looking for something like this!

---

