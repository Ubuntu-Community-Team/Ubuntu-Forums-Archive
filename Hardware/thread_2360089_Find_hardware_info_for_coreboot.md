---
title: "Find hardware info for coreboot"
date: 2017-05-01
forum: Hardware
---

### Post by piu130 on 2017-05-01
I'm trying to install coreboot in an old notebook. I can't figure out which mainboard to choose.
```
cat /sys/devices/virtual/dmi/id/board_vendor
``` returns Dell Inc.
Which is not listed in coreboot. But I think my board is supported.
```
hwinfo --short
``` returns
```
cpu:
                       Intel(R) Pentium(R) M processor 1.73GHz, 800 MHz
keyboard:
  /dev/input/event3    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      AlpsPS/2 ALPS GlidePoint
monitor:
                       JF383 LCD Monitor
graphics card:
                       Intel 915 GM
                       Intel Mobile 915GM/GMS/910GML Express Graphics Controller
sound:
                       Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
storage:
                       Intel 82801FBM (ICH6M) SATA Controller
network:
  eth0                 Dell Inspiron 6400
  wlp2s3               Intel PRO/Wireless 2915ABG [Calexico2] Network Connection
modem:
                       Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
  wlp2s3               Ethernet network interface
disk:
  /dev/ram11           Disk
  ...
  /dev/ram1            Disk
  /dev/sda             HTS548080M9AT00
  /dev/ram8            Disk
  ...
  /dev/ram4            Disk
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda5            Partition
cdrom:
  /dev/sr0             TSSTcorp DVD+-RW TS-L532B
usb controller:
                       Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
                       Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
                       Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
                       Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
                       Intel 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
bios:
                       BIOS
bridge:
                       Intel 82801 Mobile PCI Bridge
                       Intel Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller
                       Texas Instruments PCI6515 Cardbus Controller
                       Intel 82801FBM (ICH6M) LPC Interface Bridge
hub:
                       Linux Foundation 1.1 root hub
                       Linux Foundation 2.0 root hub
                       Linux Foundation 1.1 root hub
                       Linux Foundation 1.1 root hub
                       Linux Foundation 1.1 root hub
memory:
                       Main Memory
firewire controller:
                       Texas Instruments FireWire (IEEE 1394)
bluetooth:
                       Dell Wireless 350 Bluetooth
unknown:
                       FPU
                       DMA controller
                       PIC
                       Keyboard controller
  /dev/lp0             Parallel controller
                       PS/2 Controller
                       Unclassified device
                       ...
                       Unclassified device
  /dev/ttyS0           16550A
```
Any ideas? How can I find this infos?
I have latest Xubuntu installed.

---

### Post by mörgæs on 2017-05-03
+1 for Coreboot. Please post the results when you have tried it.

Does ```
sudo lshw -sanitize
``` give more detailed information?

---

### Post by piu130 on 2017-05-03
I generated this report yesterday with a ubuntu gui tool:

Plain: [https://paste.ubuntu.com/24503947/](https://paste.ubuntu.com/24503947/)
HTML: [https://paste.ubuntu.com/24503945/](https://paste.ubuntu.com/24503945/)

---

### Post by bobbyhernandez on 2017-05-03
Is This Working ???? :P

---

### Post by Yellow Pasque on 2017-05-03
I don't see any Dell laptops in their list of supported boards/laptops: [https://www.coreboot.org/Supported_Motherboards](https://www.coreboot.org/Supported_Motherboards)
Heck, I don't even see the Intel 915/ICH6 chipsets listed as supported: [https://www.coreboot.org/Supported_Chipsets_and_Devices](https://www.coreboot.org/Supported_Chipsets_and_Devices)

Google keeps producing the model number N8716 for the latitude d510 mainboard.

---

### Post by piu130 on 2017-05-04
Ok that's what I wanted to know. How did you find out the chipset/device? And which values did you compare with it in 'Supported Chipsets and Devices'?

---

### Post by mörgæs on 2017-05-04
> **piu130 said:**
> How did you find out the chipset/device?

You would have found motherboard info and info of your devices yesterday using the lshw command in the post above.

---

### Post by Yellow Pasque on 2017-05-04
> **piu130 said:**
> How did you find out the chipset/device? 
It's in the output you gave.

> And which values did you compare with it in 'Supported Chipsets and Devices'?
I'm not sure what you mean. The northbridge is Intel 910/915GM. The southbridge is 82801FBM/ICH6. They're not in the list. I saw that the page is 2 years old, so I took a look at the source code, and a few newer intel NB/SB's have been added, but not yours.

---

