---
title: "More or less new to this, and want to configure graphic cards (hybrid?)"
date: 2015-05-19
forum: Hardware
---

### Post by MsKK on 2015-05-19
Hello fellow users:

I have a Dell Inspiron 14 series 5000 (5448). It came pre-installed with Windows 8.1 but I installed Ubuntu 14.04.2 (64 bits) over it (NOT dual) from USB. I'm right now configuring it, but I found that I have no clue what to do about the graphic cards. It comes with an integrated Intel GMA HD Graphics 5500 and a AMD Radeon R7 M265. Sadly, I don't know much about this. I tried to install the proprietary fglrx-updates drivers (via Software & updates -> additionally drivers) but after the reboot, ubuntu didn't load and it told me I had to use the default, so I reverted to using X.org X server (see picture). I don't know if now I have to delete stuff or download Catalyst or what. I've been reading about it, but it gets too technical too fast, and I can't follow. If someone could explain to me what I should do and why, I would be very grateful. If you need any additional information, don't hesitate to ask. Thank you in advance. :p

[IMG]http://i.imgur.com/Gl74TRl.png?1[/IMG] 
 
my lspci is

```
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
03:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
04:00.0 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] Opal XT [Radeon R7 M265]

```

---

