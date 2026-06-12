---
title: "acer v3-575-50td wifi driver"
date: 2016-06-17
forum: Hardware
---

### Post by rev-matthewagilmore on 2016-06-17
I just got the v3-575-50td by acer. Since I been using linux, I have grow to dislike  windows more and more and don't wish to keep in on my laptop.However, i need a laptop that I can use and with out internet. I need to it for school please help.

---

### Post by ajgreeny on 2016-06-17
> **rev-matthewagilmore said:**
> I just got the v3-575-50td by acer. Since I been using linux, I have grow to dislike  windows more and more and don't wish to keep in on my laptop.However, i need a laptop that I can use and with out internet. I need to it for school please help.
Hi Mathew, and welcome to the forum.
You are obviously able to get Ubuntu-gnome to run on that machine, assuming the images are of that machine running, but I assume you are unable to get wifi to work.
However, to help us more it will be very helpful if you can open a terminal in Ubuntu and run command ```
lspci
``` and then copy back the output here in code tags.

Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by rev-matthewagilmore on 2016-06-17
```
matti@matti-Aspire-V3-575:~$ lspci
00:00.0 Host bridge: Intel Corporation Sky Lake Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Sky Lake Integrated Graphics (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
02:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)
```

see it pics up the wireless driver  and gnome-ubuntu is uptodate

---

### Post by rev-matthewagilmore on 2016-06-17
this fixed it
[http://askubuntu.com/questions/607707/ath10k-installation](http://askubuntu.com/questions/607707/ath10k-installation)

---

