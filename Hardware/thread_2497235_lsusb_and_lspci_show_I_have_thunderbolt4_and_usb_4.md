---
title: "lsusb and lspci show I have thunderbolt4 and usb 4. But the manufacurer says I don't."
date: 2024-04-27
forum: Hardware
---

### Post by nola-guy on 2024-04-27
lsusb and lspci seem to show I have usb4 and thunderbolt. The manufacturer says it doesn't and the usb-c is a 10gb port.. Here is my lsusb and lspci output with all ports occupied by devices matching the port speed. Can someone help me understand what I have? It's a 12th Gen Intel© Core&#8482; i5-1235U × 10 mini pc. Here is lsusb and lspci output with all ports occupied with devices matching port speed>

***@***-SEi12:~$ lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 10000M
    |__ Port 2: Dev 2, If 0, Class=Mass Storage, Driver=usb-storage, 5000M
    |__ Port 3: Dev 4, If 2, Class=Vendor Specific Class, Driver=, 5000M
    |__ Port 3: Dev 4, If 0, Class=Wireless, Driver=rndis_host, 5000M
    |__ Port 3: Dev 4, If 1, Class=CDC Data, Driver=rndis_host, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/12p, 480M
    |__ Port 1: Dev 7, If 0, Class=Mass Storage, Driver=uas, 480M
    |__ Port 5: Dev 2, If 2, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 5: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 5: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 12M
    |__ Port 6: Dev 8, If 0, Class=Audio, Driver=snd-usb-audio, 480M
    |__ Port 6: Dev 8, If 1, Class=Audio, Driver=snd-usb-audio, 480M
    |__ Port 7: Dev 4, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 7: Dev 4, If 1, Class=Wireless, Driver=btusb, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 20000M/x2
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/1p, 480M
***@888-SEi12:~$ lsusb
Bus 004 Device 004: ID 04e8:6864 Samsung Electronics Co., Ltd GT-I9070 (network tethering, USB debugging enabled)
Bus 004 Device 002: ID 154b:0095 PNY USB 3.0 FD
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 8087:0029 Intel Corp. AX200 Bluetooth
Bus 003 Device 008: ID 0bda:4e27 Realtek Semiconductor Corp. USB Audio
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 007: ID 6655:a583 Best Buy NS-PCNVMEHDE(-C)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
***@***-SEi12:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 4601 (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Device 46a8 (rev 0c)
00:06.0 PCI bridge: Intel Corporation 12th Gen Core Processor PCI Express x4 Controller #0 (rev 04)
00:0d.0 USB controller: Intel Corporation Alder Lake-P Thunderbolt 4 USB Controller (rev 04)
00:14.0 USB controller: Intel Corporation Alder Lake PCH USB 3.2 xHCI Host Controller (rev 01)
00:14.2 RAM memory: Intel Corporation Alder Lake PCH Shared SRAM (rev 01)
00:16.0 Communication controller: Intel Corporation Alder Lake PCH HECI Controller (rev 01)
00:17.0 SATA controller: Intel Corporation Alder Lake-P SATA AHCI Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation Device 51b8 (rev 01)
00:1c.4 PCI bridge: Intel Corporation Device 51bc (rev 01)
00:1c.6 PCI bridge: Intel Corporation Device 51be (rev 01)
00:1f.0 ISA bridge: Intel Corporation Alder Lake PCH eSPI Controller (rev 01)
00:1f.3 Audio device: Intel Corporation Alder Lake PCH-P High Definition Audio Controller (rev 01)
00:1f.4 SMBus: Intel Corporation Alder Lake PCH-P SMBus Host Controller (rev 01)
00:1f.5 Serial bus controller: Intel Corporation Alder Lake-P PCH SPI Controller (rev 01)
01:00.0 Non-Volatile memory controller: Micron/Crucial Technology P2 NVMe PCIe SSD (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
04:00.0 Network controller: Intel Corporation Wi-Fi 6 AX200 (rev 1a

I don't want to buy a Thunderbolt device just to find it won;t work. 

Thanks for the help.

---

### Post by nola-guy on 2024-04-27
\the cpu is a 12th Gen Intel© Core&#8482; i5-1235U × 10

---

### Post by #&amp;thj^% on 2024-04-27
Please show this:
```
 lsmod | grep thund

### Mine Dose.
intel_wmi_thunderbolt    16384  0
thunderbolt           512000  0
wmi                    32768  4 video,intel_wmi_thunderbolt,wmi_bmof,think_lmi

```

---

### Post by nola-guy on 2024-04-28
I got no response. So I guess Linux is not loading the Thunderbolt module.

---

### Post by #&amp;thj^% on 2024-04-28
Or Thunderbolt dose not exist on your machine, If it truly was capable, or the hardware is there, it would show.
Sorry to deliver the bad news, but now you won't waste your hard earned money on a Thunderbolt Dock.

---

### Post by MAFoElffen on 2024-04-28
Well, if you go to the Intel CPU spec page for that CPU, the CPU itself has Thunderbolt 4 support, so it itself is capable of supporting it, but... Just because the CPu supports somethings, doesn't mean the BIOS or the Motherboard that CPU is installed on supports it.

That is the first thing I thought of.

Next, in your output (please use CODE Tags when posting commands or raw output)... I see USB3.2. I saw "rev.4", meaning 'revision 4', but I didn't really see 'USB 4.0'. Am I missing that? If so, maybe you could highlight that in Red so I can see it. (I am getting old.)

---

