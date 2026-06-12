---
title: "Bluetooth in Ubuntu 11.10 on HP laptop"
date: 2012-09-04
forum: Hardware
---

### Post by radwa16 on 2012-09-04
Hi
I have an HP laptop and for about a year now have never been able to get it to work with Ubuntu 10 so I upgraded yesterday to 11.10 thinking it would do the trick, but it still won't work. 
I have tried this:

sudo apt-get install bluez python-gobject python-dbus
then,
hcitool dev

and all I get is 
Devices:
and a blank space after that. When I open up Bluetooth Manager, it says not devices connected, but I am POSITIVE that my laptop has a built-in bluetooth, because it was working before on Windows.

Any help is appreciated.
Thanks,
Radwa

---

### Post by gordintoronto on 2012-09-04
What model of HP laptop? Can you copy/paste the output of lspci and lsusb? What device are you trying to connect by bluetooth?

---

### Post by radwa16 on 2012-09-05
Thanks :)I also tried yesterday upgrading to 12.04, same problem exists. The laptop is HP G72-b66US and I am trying to connect it to my phone "Samsung F480"

This is the output of lspci

root@Radwa-Notebook:/home/radwa# lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
7f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
7f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)


root@Radwa-Notebook:/home/radwa# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 5986:0149 Acer, Inc

---

### Post by gordintoronto on 2012-09-05
HP's specs for your computer are on this page:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02503091&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=4308570](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02503091&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=4308570)

There is no mention of Bluetooth.

Are you sure your phone was not connecting by WiFi?

---

