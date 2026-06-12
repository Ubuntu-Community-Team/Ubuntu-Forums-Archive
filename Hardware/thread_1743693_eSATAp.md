---
title: "eSATAp"
date: 2011-04-29
forum: Hardware
---

### Post by nexterday on 2011-04-29
**Solved:** eSATAp from laptops only provides 5V, which can only power 2.5" HDDs, not 3.5" (which need 12V). /facepalm


I just bought an eSATAp cable ([http://www.newegg.com/Product/Product.aspx?Item=N82E16812270245&Tpk=usata-136](http://www.newegg.com/Product/Product.aspx?Item=N82E16812270245&Tpk=usata-136)) for some working hard drives, however on plug in, I do not hear or feel the hard drive spin up, nor do I see anything show up in dmesg since boot related to this event.

I was under the impression that eSATAp provides power and thus is the only thing I need to plug into the hard drive to at least get it to spin up. Is this correct?

Do I need an extra kernel module for this to work, or should this work out of the box?

I tried what was suggested [http://ubuntuforums.org/showthread.php?t=1678364&highlight=esatap](http://ubuntuforums.org/showthread.php?t=1678364&highlight=esatap)
(power cycling) but no luck. BIOS says eSATA is enabled as far as I can tell. I can plug my mouse into this port, and it works (since eSATAp is backward compatible with USB).

I'm using Ubuntu 10.10 (Maverick), 64-bit. lspci and lsusb:

```
eric@desky:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
03:00.0 CardBus bridge: Ricoh Co Ltd Device e476 (rev 02)
03:00.1 SD Host controller: Ricoh Co Ltd Device e822 (rev 03)
03:00.4 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 03)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

eric@desky:~$ lsusb
Bus 002 Device 006: ID 047d:1029 Kensington Mouse*in*a*Box Optical Elite
Bus 002 Device 004: ID 0a5c:5800 Broadcom Corp. BCM5880 Secure Applications Processor
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Thanks,

-Eric

---

