---
title: "Installed on Surface Book 2 - two issues"
date: 2020-04-24
forum: Hardware
---

### Post by fballem on 2020-04-24
First of all, I was successful in installing Ubuntu 20.04 on a Surface Book 2 - it went quite smoothly.

I have been away from ubuntu for several years, so I have forgotten a great deal:

Issue 1: The built-in webcam does not work at all. Does anyone know of drivers and how to fix?

Issue 2: Is touch screen supported in Ubuntu?

I know this is brief - tell me what you need to know and how to get the information - please provide specific instructions.

Many thanks!

---

### Post by CelticWarrior on 2020-04-24
I have ZERO experience with such hardware so helping you with issue #1 is out of the question, I know nothing about it.
Regarding #2: Yes, most touchscreens are natively supported. If yours isn't working you should google about your exact model + Ubuntu to see what comes up. Maybe there are "fixes" and/or "workarounds" already tested for earlier Ubuntu releases that may or may not work in Ubuntu 20.04.

---

### Post by fballem on 2020-04-25
I have had to go back to Windows because of the webcam issue (cannot live without it). The webcam is an Intel AVStream 2500 built-in. I have been googling to look for a driver that will work in Ubuntu, but apparently none exist. I could have lived without the touch screen, but I do need a working webcam.

---

### Post by mörgæs on 2020-04-25
If you want to give the webcam a second try then please do a live boot, run **lsusb** and post the result in CODE tags.

---

### Post by fballem on 2020-04-27
Hi,

```

Bus 002 Device 003: ID 045e:0943 Microsoft Corp. L1 USB3 Gen1 Hub
Bus 002 Device 002: ID 045e:0941 Microsoft Corp. L1 USB3 Gen1 Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 045e:091e Microsoft Corp. XBOX ACC
Bus 001 Device 007: ID 1286:204c Marvell Semiconductor, Inc. Bluetooth and Wireless LAN Composite Device
Bus 001 Device 005: ID 045e:0922 Microsoft Corp. 
Bus 001 Device 006: ID 0781:5202 SanDisk Corp. 
Bus 001 Device 004: ID 045e:0944 Microsoft Corp. L1 USB2 Hub
Bus 001 Device 002: ID 045e:0942 Microsoft Corp. L1 USB2 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

In Device Manager (Windows 10), the camera is identified as an Intel AVStream Camera 2500. I don't see anything like that on the list and I am suspecting that it is not using a USB interface. I can't seem to find a lot of detail on how the camera is connected, but that is most likely a function of me not knowing what I am doing.

---

### Post by CelticWarrior on 2020-04-27
Try also **lspci** .

---

### Post by fballem on 2020-05-05
```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 08)
00:05.0 Multimedia controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Imaging Unit (rev 01)
00:13.0 Non-VGA unclassified device: Intel Corporation Sunrise Point-LP Integrated Sensor Hub (rev 21)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:14.3 Multimedia controller: Intel Corporation Device 9d32 (rev 01)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:15.2 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #2 (rev 21)
00:15.3 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #3 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:16.4 Communication controller: Intel Corporation Device 9d3e (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #1 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1d.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #9 (rev f1)
00:1e.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO UART Controller #0 (rev 21)
00:1f.0 ISA bridge: Intel Corporation Sunrise Point LPC Controller/eSPI Controller (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88W8897 [AVASTAR] 802.11ac Wireless
02:00.0 3D controller: NVIDIA Corporation GP106M [GeForce GTX 1060 Mobile] (rev a1)
03:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM961/PM961

```

---

### Post by mörgæs on 2020-05-07
Another case like yours:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1737536](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1737536)

I don't know much about IPU3 so I can only suggest that you begin googling on your own.

By the way, which webcam applications have you tried?

---

### Post by fballem on 2020-06-24
I have tried skype and the camera app.

As for patching Linux to support the webcam and touch that is beyond me.

---

