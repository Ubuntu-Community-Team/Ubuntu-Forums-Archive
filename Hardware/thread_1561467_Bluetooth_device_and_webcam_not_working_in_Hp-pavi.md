---
title: "Bluetooth device and webcam not working in Hp-pavilion dm4"
date: 2010-08-26
forum: Hardware
---

### Post by grvsaxena419 on 2010-08-26
Hello all,

I am having problem in my laptop in using bluetooth device and webcam.
I have installed ubuntu 10.04 
and when I open Bluetooth preferences it says your computer does not have any bluetooth adapters plugged in.
Also I am unable to find any way to detect my webcam in ubuntu.
Please Help...!!:(

---

### Post by Mansor on 2010-08-30
Hi I've also a hp pavilion dm4, webcam works out of the box.
Try to install cheese.
I'm no able to use bluetooth, I'm using propietary drivers for WiFi. 

Anyone has a clue how I can activate bluetooth?

lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


lsusb
Bus 002 Device 004: ID 10f1:1a28  
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 138a:0005 DigitalPersona, Inc 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Cheers

---

### Post by grvsaxena419 on 2010-09-02
Yes webcam is working with cheese .
thanks a lot :)

bluetooth  and wifi is working in ubuntu after instaling properietory drivers .
If  bluetooth is not working you try enabling it using hp software in  windows and then restart and use wifi button on laptop to turn bluetooth  and wifi on.
It worked for me 
also i am trying a way to use my  fingerprint reader in ubuntu as it works in windows

---

### Post by Mansor on 2010-10-18
If you don't have windows? How I can enable bluetooth?

Thanks

---

