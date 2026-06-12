---
title: "SparkLan WPER-101GN(BT)"
date: 2010-09-29
forum: Hardware
---

### Post by rtomakov on 2010-09-29
I really need some help with this card under lucid (tried desktop and netbook and amd64 version) installed on emachines e527 laptop.

Now, it is Sparklan WPER-101GN wifi combo card with bluetooth (3.0+hs). It has ralink rt3090**bc4** chipset (ralink wlan +  motorola bluetooth part).

WiFi  works with rt3090-dkms package (latest, from marcus-tisoft ppa), but I cant get 
bluetooth part to work.

System recognize bluetooth device but it doesnt work - computer is not visible to other devices nor it can find any other bluetooth device, no file transfer nor anything else what bluetooth stuff usually can do. 

I have installed all bluetooth, bluez... packages, but nothing help.
And...yes (I hate to say this) under windows it works fine.

Can anyone help, please, I really dont want to use windows only because bluetooth (that I need just sometimes) doesnt work.

---

### Post by pervert on 2010-11-27
I am actually waiting for mine to arrive, and I thought there'd be support quite handily with ubuntu via bluez and wifichip driver. Once the card finally arrives, hopefully you have a solution. If not, i'll try and get it up and running and post my results here.

---

### Post by Fafler on 2010-11-27
Post output from lspci and lsusb. It's likely as simple as the device and vendor ID's aren't recognised by the driver.

---

### Post by fgiava on 2010-12-03
I have the same problem on my hp4320s laptop. The RT3090BC4 seems to work correctly but on bluetooth side is not possible discover others bluetooth devices nor anything else. I have tried to investigate with hciconfig but all the standard configuration parameters are ok; I think the problem is in the RF radio layer shared with WiFi radio.

I discovered  a way to get this card working on Linux; is not a real solution but maybe this 'workaround' can help us to find a real solution.

My laptop comes with Win7 preinstalled, the RT3090bc4 works well under win and so it seem to have the correct configuration. Well, turn on win and the WiFi + Bluetooth also, now press the wireless button, the RT3090 is powered off. Now you can shutdown windows.

The RT090BC4 probably stores some parameters in its eeprom because after this operation the bluetooth works perfectly in Linux also. Moreover, the only way to loose the Linux bloetooth functionality   is run again windows and do a shutdown operation with the bluetooth switched on.



Any suggestions or ideas would be much appreciated...



To test I used Ubuntu 10.04 32b kernel 2.6.32.26; blueZ 4.60; driver RT3090PCIe 2.4.0.2 from Ralink and firmware rt2860.bin Ver-26 from Ralink

---

### Post by Hcimor on 2011-07-01
I have same problem on my HP 4520s laptop wirh rt3090bc4. Ubuntu 11.04

Can anybody help me?

---

### Post by mugwash on 2011-10-02
Has anyone found a solution yet? I have the same situation as fgiava. Bluetooth on Ubuntu only seems to work if I boot Windows 7 and switch the card off (using fn key) before rebooting into Ubuntu.

I'm running 11.04 but I tried a live image of 11.10 beta 2 and it seems the same.

I get the same results from lspci and lsusb regardless of whether I've done the "Windows switching" workaround. The wi-fi part of this hybrid card (02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe 
and
Bus 001 Device 004: ID 148f:1000 Ralink Technology, Corp. ) is always detected and fully functional but I can't seem to find the bluetooth part registered in Linux...

Here's what I get from lspci:
```

ben@mr-shinyface:~$ sudo lspci
[sudo] password for ben: 
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
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
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon HD 5600 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
7f:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
7f:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
7f:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
7f:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
7f:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
7f:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
7f:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
7f:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
7f:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
7f:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
7f:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```And here's what I get from lsusb:
```

ben@mr-shinyface:~$ sudo lsusb
Bus 002 Device 004: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 138a:0005 DigitalPersona, Inc 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 148f:1000 Ralink Technology, Corp. 
Bus 001 Device 003: ID 046d:c051 Logitech, Inc. G3 (MX518) Optical Mouse
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I hope someone can help
Thanks :)

---

