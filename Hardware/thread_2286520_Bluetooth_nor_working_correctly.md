---
title: "Bluetooth nor working correctly"
date: 2015-07-12
forum: Hardware
---

### Post by encefalocardia on 2015-07-12
Hi. I'm using a HP Classmate Notebook. This device, says the HP brochure, have an hybrid Wireless/Bluetooth chip. The thing is, I think the Bluetooth device is detected. rfkill list not hardware or software blocks and is indeed detecting a bluetooth device at hci0. Also, the bluetooth applet is indeed activated and allows me to turn on and off the device, but it always happens the same, no device is detected nor any device can detect it.

Here is the output of lspci -nn

> 
00:00.0 Host bridge [0600]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register [8086:0f00] (rev 0a)
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display [8086:0f31] (rev 0a)
00:13.0 SATA controller [0106]: Intel Corporation Device [8086:0f23] (rev 0a)
00:14.0 USB controller [0c03]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series USB xHCI [8086:0f35] (rev 0a)
00:1a.0 Encryption controller [1080]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine [8086:0f18] (rev 0a)
00:1b.0 Audio device [0403]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller [8086:0f04] (rev 0a)
00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:0f48] (rev 0a)
00:1c.1 PCI bridge [0604]: Intel Corporation Device [8086:0f4a] (rev 0a)
00:1f.0 ISA bridge [0601]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit [8086:0f1c] (rev 0a)
00:1f.3 SMBus [0c05]: Intel Corporation Device [8086:0f12] (rev 0a)
01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)


This is the dmesg output:

> 
[    3.240904] usb 1-3.3: Product: Bluetooth Radio 
[    8.889618] Bluetooth: Core ver 2.20
[    8.889664] Bluetooth: HCI device and connection manager initialized
[    8.889674] Bluetooth: HCI socket layer initialized
[    8.889682] Bluetooth: L2CAP socket layer initialized
[    8.889699] Bluetooth: SCO socket layer initialized
[   20.199364] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.199372] Bluetooth: BNEP filters: protocol multicast
[   20.199385] Bluetooth: BNEP socket layer initialized
[   20.302963] Bluetooth: RFCOMM TTY layer initialized
[   20.302981] Bluetooth: RFCOMM socket layer initialized
[   20.302994] Bluetooth: RFCOMM ver 1.11


Im finding conflicting information on the internet. While every spec brochure about this machine indeed states that it has a Bluetooth 4.0 chip some sites report that the Realtek RTL8723BE handles this others are saying that the Bluetooth controller is a non-specified model by Lite-on/Azurewave.

I've been trying everything, from Ubuntu 14.04 to 15.10 alpha, to the 3.13 kernel to the latest 3.19 to no avail.

Any suggestions?

---

### Post by jeremy31 on 2015-07-12
Look at Pilot6's answer [http://askubuntu.com/questions/644073/bluetooth-not-detecting-any-devices](http://askubuntu.com/questions/644073/bluetooth-not-detecting-any-devices)

It should work for you

---

### Post by encefalocardia on 2015-07-12
> **jeremy31 said:**
> Look at Pilot6's answer [http://askubuntu.com/questions/644073/bluetooth-not-detecting-any-devices](http://askubuntu.com/questions/644073/bluetooth-not-detecting-any-devices)

It should work for you

That did the trick! And to think I sacrificed a LTS installation when all of this could be solved asking here first.

Anyway, thats my fault, thanks a lot pal!

---

