---
title: "New desktop system build (April 18) issues"
date: 2020-05-16
forum: Hardware
---

### Post by patrick_g2 on 2020-05-16
This is the Hardware config which is installed in a case that is nothing but air vents and stays pretty cool

Motherboard: Gigabyte B450 AORUS M (AMD Ryzen AM4/M.2 Thermal Guard/HDMI/DVI/USB 3.1 Gen 2/DDR4/Micro ATX/Motherboard)
BIOS Information
Version: F50
Date: 11/29/2019
ID: 8A16BG06

CPU: AMD Ryzen 5 3600X 6-Core, 12-Thread Unlocked Desktop Processor with Wraith Spire Cooler
Part: 100-100000022BOX

Memory: OLOy DDR4 RAM 32GB (2x16GB) Warhawk Aura Sync RGB 2666 MHz CL19 1.2V 288-Pin
PC4-21333 19-19-19-43

Boot Drive: Silicon Power 512GB NVMe M.2 PCIe Gen3x4 2280 TLC R/W up to 3,400/2,300MB/s SSD (P/N: SU512GBP34A80M28AB mDL: a80)

Video: Gigabyte GeForce GT 710 2GB Graphic Card and Support PCI Express 2.0 X8 Bus Interface. Graphic Cards 
Model: GV-N710D5-2GL

WiFi: EDUP WiFi 6 WiFi Adapter AX 3000 Mbps AX200 Dual Band 5GHz/2.4GHz PCI-E Wireless WiFi Network Adapter Card with Bluetooth 5.0 64-bit, EP-AC9636

Ubuntu 19.10 
VLC media player
OBS Studio
Blender

Yes it is snappy and It has been work great but has developed a couple issues:

1. Wifi: a couple weeks ago the wifi connection started freezing periodically. I plugged in a direct cable to the router and that helps, but I still get the occasional communications freeze

2. Video: I built this machine specifically to support video production work: creating .mp4 and youtube videos. It has been doing a great job until 2 days ago when I started getting audio stuttering. Yesterday it progressed to video stuttering. This morning watching a video, the image started to pixelating periodically and it appears to continue degrading.

I have reloaded the NVIDIA Driver Version 435.21 completely. I have been monitoring NVIDIA X Server: the Video card environment, it appears the temp runs between 42c and 51c

Anyone have any ideas on what might be going on? I am thinking that the Video card might be slowly failing. Alternatively, is the entire system stuttering?

---

### Post by Autodave on 2020-05-17
Where did you get the driver for the nVidia card from?

---

### Post by patrick_g2 on 2020-05-17
It downloaded when I asked for the driver updates. It is from The X.Org Foundation and has all the correct info in the GEForce GT710

---

### Post by CelticWarrior on 2020-05-17
> **patrick_g2 said:**
> It downloaded when I asked for the driver updates. It is from The X.Org Foundation and has all the correct info in the GEForce GT710

The X.org driver is nouveau, the default open-source driver for Nvidia cards. It is NOT the Nvidia proprietary driver that you need for the hard work you're demanding from the card and you said you have but apparently don't? I'm confused now...

Also update your UEFI firmware and disable Secure Boot. This assumes you installed Ubuntu properly in UEFI mode. If Legacy the Secure Boot doesn't apply but also all sorts of problems can and should be expected.

---

### Post by patrick_g2 on 2020-05-17
The only drivers Gigabyte offers for the card are for Windows 7 & 10. The X.org is the only Linux driver I could find for the card. 
The UEFI/BIOS firmware is the last one released.

Let me re-state that the system was working great until about a week ago, then it started acting up.

---

### Post by CelticWarrior on 2020-05-17
Please open Additional Drivers and check what is select and what is offered. We all know that the manufacturers do that but Ubuntu provides drivers which are, btw, a lot easier to install than the Windows ones. But again: Disable Secure Boot.

---

