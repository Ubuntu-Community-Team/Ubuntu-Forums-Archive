---
title: "Laptop Acer E1-572G-74508G1TMnkk Problem with Ethernet controller"
date: 2013-12-29
forum: Hardware
---

### Post by denis21-ru on 2013-12-29
Ethernet controller doesn't work. I watch it in stdout lspci/lshw, but not in ifconfig. 

```
00:00.0 Host bridge: Intel Corporation Device 0a04 (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0a16 (rev 09)
00:03.0 Audio device: Intel Corporation Device 0a0c (rev 09)
00:14.0 USB controller: Intel Corporation Device 9c31 (rev 04)
00:16.0 Communication controller: Intel Corporation Device 9c3a (rev 04)
00:1b.0 Audio device: Intel Corporation Device 9c20 (rev 04)
00:1c.0 PCI bridge: Intel Corporation Device 9c14 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Device 9c16 (rev e4)
00:1c.4 PCI bridge: Intel Corporation Device 9c18 (rev e4)
00:1d.0 USB controller: Intel Corporation Device 9c26 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 9c43 (rev 04)
00:1f.2 SATA controller: Intel Corporation Device 9c03 (rev 04)
00:1f.3 SMBus: Intel Corporation Device 9c22 (rev 04)
01:00.0 Ethernet controller: Broadcom Corporation Device 16b3 (rev 01)
01:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 01)
02:00.0 Network controller: Atheros Communications Inc. Device 0036 (rev 01)
03:00.0 Display controller: Advanced Micro Devices [AMD] nee ATI Device 6600
```

I found the problem, and it would seem the decision - patch for kernel in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1242610](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1242610)
I used it, but when I try to compile the kernel version 3.12.6 I get an error - (Screenshot - [http://s28.postimg.org/96s680mjh/IMG_20131229_175215.jpg](http://s28.postimg.org/96s680mjh/IMG_20131229_175215.jpg) )
Tell me please, how can I solve this problem? Thx.

---

### Post by denis21-ru on 2014-01-01
Answer himself. :( 
My problem was solved by setting the kernel 3.13.

---

