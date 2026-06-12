---
title: "Motherboard Compatibility"
date: 2008-12-31
forum: Hardware
---

### Post by alecjw on 2008-12-31
This is probably a bit of a noobish question, but I dont know much about motherboards.
Are all motherboards compatible with any operating system? (Or more specifically ubuntu)?
Do they follow set standards like hard drives and usb memory sticks which are OS independent?

---

### Post by albinootje on 2008-12-31
> **alecjw said:**
> This is probably a bit of a noobish question, but I dont know much about motherboards.
Are all motherboards compatible with any operating system? (Or more specifically ubuntu)?
Do they follow set standards like hard drives and usb memory sticks which are OS independent?

No, unfortunately not :( But check here for example :

[http://www.fsf.org/resources/hw](http://www.fsf.org/resources/hw)
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)
[http://www.linuxcompatible.org/](http://www.linuxcompatible.org/)
[https://hardware.redhat.com/](https://hardware.redhat.com/)

And if you already have the machine, this page is very cool :
[http://kmuto.jp/debian/hcl/](http://kmuto.jp/debian/hcl/)

:)

---

### Post by Skripka on 2008-12-31
> **alecjw said:**
> This is probably a bit of a noobish question, but I dont know much about motherboards.
Are all motherboards compatible with any operating system? (Or more specifically ubuntu)?
Do they follow set standards like hard drives and usb memory sticks which are OS independent?

There are 3 or 4 copmmon board form factors....about a dozen or so fairly common CPU socket types still for sale.....HDDs are now SATA-although system boards still provide legacy IDE headers.  There are too many different RAM speeds and types to care to list.


You have to know EXACTLY what you want when buying a system board:
-Board form factor
-CPU, AMD or Intel--and then worry about socket type
-MAX CPU wattage, some board don't support CPUs above 100W
-ATI or Nvidia bridges? determines if you can SLi or Crossfire graphics cards


After figuring that out you balance:
-How many PCI rails?
-How many PCIe 2.0 x16 rails?
-RAM speed?
-Max amount of RAM
-Number of SATA/IDE/USB/Firewire/e-SATA ports/headers
-On board audio?
-on board wireless?
-How good the BIOS is

There's lots of very salient details.  Usually if you buy a board-you can run an OS on it (at the least Windows)-whether or not all it's features are supported under Linux is another matter.

---

### Post by albinootje on 2008-12-31
For motherboard + Linux, see also here :
[http://en.wikipedia.org/wiki/LinuxBIOS](http://en.wikipedia.org/wiki/LinuxBIOS)
---> [http://www.coreboot.org/Supported_Motherboards](http://www.coreboot.org/Supported_Motherboards)

---

### Post by Therion on 2008-12-31
IMO what you really need to do is work backwards starting WITH the motherboard.  Since everything connects TO it, this single component is what will determine the makeup of the rest of your system.  Build your new PC on paper first, starting with the mobo and then spec out what CPU, memory, and video card options it gives you and find components that are both compatible with it AND fit your budget and performance targets.  

Don't forget things like how many PCI slots you may need, whether or not you'll need IDE hard drive support and things of that nature.  The devil really IS in the details when it comes to building from scratch.

---

