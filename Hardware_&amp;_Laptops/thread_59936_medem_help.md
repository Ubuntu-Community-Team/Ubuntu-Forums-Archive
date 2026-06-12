---
title: "medem help"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by zubair on 2005-08-25
my modem is intel ham data fax voice modem.
i am using Ubuntu 5.04 "Hoary Hedgehog"  kernel 2.6.10-5-386.
please help me that how i can connect to internet through it.
list of pci devices
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0b.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV4 [RIVA TNT] (rev 0 4)
tell me also how to confogure it.
how to detect it
what driver i need.

---

### Post by az on 2005-08-25
[https://wiki.ubuntu.com/forum/hardware/modem](https://wiki.ubuntu.com/forum/hardware/modem)

[https://wiki.ubuntu.com/forum/hardware/smartlink](https://wiki.ubuntu.com/forum/hardware/smartlink)

If that does not work, install build-essential and linux-headers-2.6.10-5-386 (from you cd)  download the intel ham linux drivers from the intel website and untar the file in your ubuntu system (from a terminal and read the readme as to how to compile and install that driver.  

The sl-modem drivers will probably work, though.

---

