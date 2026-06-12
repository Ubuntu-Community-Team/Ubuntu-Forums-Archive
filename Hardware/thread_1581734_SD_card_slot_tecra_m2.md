---
title: "SD card slot tecra m2"
date: 2010-09-25
forum: Hardware
---

### Post by palz2015 on 2010-09-25
I have a Toshiba Tecra M2 (about 9 years old) with ubuntu 10.04. My SD slot doesn't detect any cards. Is there a driver?

Here's lspci:
```
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 32M/64M] (rev a1)
02:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:09.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
```

---

### Post by palz2015 on 2010-09-25
bump

---

### Post by palz2015 on 2010-09-25
Come on, no one knows?

---

### Post by CFury on 2010-09-25
I know there's a work-around/solution for Richo & Intel cardbus devices, however I'm not sure about the Toshibas.  I have an HP with a micro cardbus and am in the same boat with my SD card reader.  Sorry I couldn't be of any more help.

---

### Post by palz2015 on 2010-10-09
Another toshiba (satellite) with Wubi read SD cards fine. Weird...

---

### Post by IcarusR on 2010-10-10
> Another toshiba (satellite) with Wubi read SD cards fine. Weird...   

Only if it has the exact same cardreader chipset.

Toshiba change their hardware a lot between models.


There is no linux driver for this proprietary Toshiba  SD TypA Controller. Toshiba are not linux friendly & don't release specs for their chipsets.

See this bug report  that goes back to Ubuntu 7.04.

[http://ubuntuforums.org/showthread.php?p=9947161#post9947161]("http://ubuntuforums.org/showthread.php?p=9947161#post9947161")

---

### Post by koanhead on 2012-08-04
IcarusR's link is broken, I think he means this:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/88863](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/88863)

A little more information here:

[http://www.chiark.greenend.org.uk/~theom/electronics/toshiba-sd-controller.html](http://www.chiark.greenend.org.uk/~theom/electronics/toshiba-sd-controller.html)

I urge anyone else having this problem to subscribe to this bug report, and to communicate your displeasure to Toshiba. I will be telling them that neither I nor my company will not purchase any Toshiba products until and unless they start supporting the FLOSS community. 

I might try to get hold of the source code mentioned further down the bug report:

[http://comments.gmane.org/gmane.linux.drivers.sdhci.devel/2234](http://comments.gmane.org/gmane.linux.drivers.sdhci.devel/2234)

and see if I can build it. I'm not a driver hacker, so I don't know if I'll be able to make it happen. If I can I'll report back here.

---

### Post by pakopako on 2012-11-05
> **CFury said:**
> I know there's a work-around/solution for Richo & Intel cardbus devices, however I'm not sure about the Toshibas.  I have an HP with a micro cardbus and am in the same boat with my SD card reader.  Sorry I couldn't be of any more help.
Why can't the Ricoh/Intel work-around work for Toshiba's SD TypA Controller?

A suggestion on Windows platforms was to install "HP Secure Digital (SD) Bus Driver 6.0.4069.1 2000" -- it would allow SDHC cards to be read. Booting up via Hiren's Boot CD, the Knoppix Linux environment reads the SD reader.

Out of curiosity, what's the Ricoh/Intel workaround?

---

