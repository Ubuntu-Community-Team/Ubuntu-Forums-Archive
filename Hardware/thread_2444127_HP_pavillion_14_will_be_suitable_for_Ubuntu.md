---
title: "HP pavillion 14 will be suitable for Ubuntu?"
date: 2020-05-25
forum: Hardware
---

### Post by guymcho11 on 2020-05-25
I will get this laptop next month , and i need to know if i install Ubuntu as my main system it will work fine as network wifi and touchpad , i had hp before and didnt had any problems with Ubuntu , i wonder if it will be the same

---

### Post by CelticWarrior on 2020-05-25
Welcome.

Your question is unanswerable. There are dozens of different configurations under the "HP Pavillion 14" model name and even the same exact model number can come with slightly different hardware, namely the WiFi chipset. Most will work natively, some will need user installed drivers.

Please post a specific question if anything isn't working and give the hardware specifications.

---

### Post by guymcho11 on 2020-05-25
OPERATING SYSTEM
Windows 10 Home 64
PROCESSOR FAMILY
10th Generation Intel® Core™ i3 processor
PROCESSOR
Intel® Core™ i3-1005G1 (1.2 GHz base frequency, up to 3.4 GHz with Intel® Turbo Boost Technology, 4 MB L3 cache, 2 cores)
CHIPSET
Intel® Integrated SoC
MEMORY
8 GB DDR4-2666 SDRAM (1 x 8 GB) Transfer rates up to 2666 MT/s. 1 x 8 GB
HARD DRIVE
256 GB PCIe® NVMe™ M.2 SSD
OPTICAL DRIVE
Optical drive not included
CLOUD SERVICE
Dropbox [1]
GRAPHICS
Integrated
GRAPHICS (INTEGRATED)
Intel® UHD Graphics
PORTS
1 USB 3.1 Gen 1 Type-C™ (Data Transfer Only, 5 Gb/s signaling rate); 2 USB 3.1 Gen 1 Type-A (Data Transfer Only); 1 AC smart pin; 1 HDMI 1.4b; 1 headphone/microphone combo; 1 RJ-45
EXPANSION SLOTS
1 multi-format SD media card reader
WEBCAM
HP Wide Vision HD Camera with integrated dual array digital microphone
AUDIO FEATURES
Audio by B&O; Dual speakers; HP Audio Boost 1.0
KEYBOARD
Full-size island-style luminous gold backlit keyboard
POINTING DEVICE
HP Imagepad with multi-touch gesture support
WIRELESS
Realtek RTL8821CE 802.11b/g/n/ac (1x1) Wi-Fi® and Bluetooth® 4.2 Combo MU-MIMO supported; Miracast compatible
INPUT DEVICES
Accelerometer
NETWORK INTERFACE
Integrated 10/100/1000 GbE LAN
POWER SUPPLY TYPE
45 W Smart AC power adapter
BATTERY TYPE
3-cell, 41 Wh Li-ion

---

### Post by CelticWarrior on 2020-05-25
Realtek RTL8821CE needs user installed drivers. First try installing Ubuntu 20.04 with the option to install third-party drivers, firmware, etc. If it doesn't get installed automatically then, with an alternative internet connection (Ethernet cable, USB tethering, other...), do the following, in Terminal:

```
sudo apt install rtl8821ce-dkms
```

---

### Post by guymcho11 on 2020-05-25
Ok , and the touchpad will work ?

Thanks bro

---

### Post by CelticWarrior on 2020-05-25
> **guymcho11 said:**
> Ok , and the touchpad will work ?

It should. Post a question about it if it doesn't.

---

