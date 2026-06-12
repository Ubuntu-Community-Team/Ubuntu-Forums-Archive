---
title: "Thinkpad T420 SD-Card not working"
date: 2017-11-28
forum: Hardware
---

### Post by forty-two- on 2017-11-28
I have a Lenovo Thinkpad T420 with Xubuntu 16.04 and I have the folowing  problem: when I put an SD-Card in the internal SD-Cardreader nothing  happens. I tried running **dmesg** and get the following results:

```

[   78.900025] mmc0: error -110 whilst initialising SD card
[   79.076097] mmc0: error -110 whilst initialising SD card 
[   79.260818] mmc0: error -110 whilst initialising SD card
[   79.451745] mmc0: error -110 whilst initialising SD card

```

running **lsusb** gives:

```

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 001 Device 003: ID 04f2:b221 Chicony Electronics Co., Ltd integrated camera
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

running **lspci** gives


```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)
0d:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 08)

```

also I observed the same problem with different SD-Cards, hoever they all work on any other machine

thanks for your help,

  Cheers f-t!

---

