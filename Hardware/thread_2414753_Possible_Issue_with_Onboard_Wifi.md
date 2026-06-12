---
title: "Possible Issue with Onboard Wifi"
date: 2019-03-14
forum: Hardware
---

### Post by maxoa on 2019-03-14
Greetings all,
I have a plain-Jane Acer with an Atheros onboard wifi. My wifi is dropping out (seemingly) every ten minutes. :(   I have tried a little bit of tuning my power settings, in case it was an issue... 

But now I recently got an external USB wifi (which may be listed below). I want to turn off the internal wifi onboard and test if it is really my laptop or my router/gateway.

Can someone guide me on how to turn off the internal wifi, I woule like to test if the problem is my router or old wifi.
Cheers

```

$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Skylake GT2 [HD Graphics 520] (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point-LP LPC Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Network controller: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)    # internal wifi ???

lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 0bda:57cc Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 04f3:222a Elan Microelectronics Corp. 
Bus 001 Device 004: ID 0489:e09f Foxconn / Hon Hai 
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n    # my external wifi ???
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

