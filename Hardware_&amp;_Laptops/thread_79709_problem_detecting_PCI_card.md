---
title: "problem detecting PCI card"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by tbobo05 on 2005-10-20
I am using the stock 2.6.10-5-386 kernel and I am having problems with detecting a PCI card that i recently installed.  The card is a Lucent/Agere DSP1648c based chipset modem.  I have the drivers installed for the card, but for some reason the kernel is not detecting the card itself.  I have checked both the card and the slot, both are functional.  I am including the output of lspci.  Is there anyway that I can manually force the kernel to detect the hardware?  

```
:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0b.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
0000:00:0f.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)
0000:01:00.0 VGA compatible controller: S3 Inc. 86c368 [Trio 3D/2X] (rev 02)
```

Any help would be appreciated, if any other info is needed just let me know.  Thanks.

---

