---
title: "Lenovo laptop SD card reader not working"
date: 2011-07-06
forum: Hardware
---

### Post by Marzata on 2011-07-06
SD card reader is not working on a brand new Lenovo G570 laptop. Any idea how to fix it? 

Here are the outputs of lsusb and lspci: 

$ lsusb
Bus 002 Device 004: ID 5986:0292 Acer, Inc
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp.
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor
Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation
Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset
Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB
Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High
Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI
Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI
Express Root Port 2 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB
Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC
Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6
port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus
Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast
Ethernet (rev c1)
07:00.0 Network controller: Atheros Communications Inc. AR9285
Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by aruizcon on 2011-07-11
I have the same problem too ;-)

---

### Post by jvgeli on 2011-07-11
same here. Its a realtek multi card reader.

---

### Post by Marzata on 2011-07-11
And the internal microphone on a new Lenovo G570 is not working too with Ubuntu 11.04. Same there?

---

### Post by aruizcon on 2011-07-16
> **Marzata said:**
> And the internal microphone on a new Lenovo G570 is not working too with Ubuntu 11.04. Same there?

See:
[http://ubuntuforums.org/showpost.php?p=11053798&postcount=4](http://ubuntuforums.org/showpost.php?p=11053798&postcount=4)

---

### Post by freechelmi on 2011-07-19
> **Marzata said:**
> SD card reader is not working on a brand new Lenovo G570 laptop. Any idea how to fix it? 


Realtek sent a driver , not tested for now .

See this thread 

[http://ubuntuforums.org/showpost.php?p=11062960&postcount=6](http://ubuntuforums.org/showpost.php?p=11062960&postcount=6)

---

### Post by Amorget on 2011-07-19
Just to cross post, the driver in the other post works!

---

### Post by aruizcon on 2011-07-26
Great!

Drivers for RTS5139 works perfectly on Lenovo G570!!!

Thanks.

---

### Post by ionospheric on 2012-03-09
> **aruizcon said:**
> Great!

Drivers for RTS5139 works perfectly on Lenovo G570!!!

Thanks.

same here.

Linux rocks!!!

---

### Post by Marzata on 2012-03-09
Lenovo G570 is a crap. Avoid it.

---

