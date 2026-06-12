---
title: "Dell Precision M90 display issues"
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by casperlingus on 2006-08-14
I've always had problems with dual monitors and Ubuntu (especially with nVidia cards).  Why does this have to be so hard???

Right now I use Windows mainly because the DVI connection to external monitor works fine and I can work with one monitor rotated.  In Ubuntu, *I can't even convince it there is DVI output.*  Ubuntu won't even acknowledge DVI.  When I hook up analog it outputs everything to the analog connection which has terrible quality.  And for my life I can't get it to display to both screens.  In the past I've gotten dual displays to work (kind of) with Ubuntu, but there was no way to select the primary device.

Ubuntu/Linux/kernel support needs to be added so that someone can specify something like the following:

```
Screens:  2

Screen 1:  
   Device:       video card 1 
   Connection:   Analog
   Res:          1920x1200

Screen 2:  
   Device:       video card 1 
   Connection:   DVI 
   Res:          1920x1200
   Option        "RandRRotation" "on"
   Option        PRIMARY

```

Am I mistaken??  Is there already something like this.  I have followed every HOWTO I could find on the subject and never seen anything like this.  I bought "Ubuntu Hacks" and tried Xinerama and Twinview, neither of them work.

For my life I can't figure out how to select the primary device, and in this case I can't even get Ubuntu to acknowledge the DVI at all.  

Just for reference, here is my lspci output

```
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 029a (rev a1)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)0000:09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0000:0c:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
```

Casper...

---

