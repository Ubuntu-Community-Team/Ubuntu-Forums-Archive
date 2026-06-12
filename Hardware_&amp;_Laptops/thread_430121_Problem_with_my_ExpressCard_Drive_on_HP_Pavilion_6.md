---
title: "Problem with my ExpressCard Drive on HP Pavilion 6275us"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by sagui on 2007-05-01
I recently got a HP Pavilion 6275us laptop and it had vista installed (which I didn't really like), so now it's running Feisty and I have pretty much everything working (from what I can tell), except one thing:  The Expresscard TV Tuner that came with it.

Now, I think it's because the ExpressCard slot itself isn't working (Vista runs the Tuner fine) because it doesn't show up when I run lspci.  Here is the output:


[INDENT]sagui@sagui-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7400 (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:00.0 Multimedia video controller: Conexant Unknown device 8852 (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
[/INDENT]

Any ideas anyone?

---

### Post by teh.element on 2007-05-02
Have you checked for drivers for it anywhere? I dont know if you will need expresscard drivers or not... I own a HP DV9000T and was considering buying that same tuner. I would like to hear more about this.

---

### Post by sagui on 2007-05-03
Well, I did check for drivers for both the slot and the tuner card.

Turns out, I may have the slot working after all (I don't have another card to test it with).  I read that this entry:

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)

Is actually the one for the ExpressCard Reader.  I don't have any cards (other than the tuner) to try it out, so I just have to believe it.

So I guess now I just have to find a driver for the card.  Unfortunately I've come up empty on that one.

---

### Post by explemonk on 2007-05-06
I am also interested in seeing how this works out.  I just bought a dv9000 series laptop that came with the TV tuner.  Vista makes my head hurt and so I would love to get it working on Ubuntu.

---

### Post by sambahat on 2007-05-21
Are you sure it isn't this device?
Multimedia video controller: Conexant Unknown device 8852 

I have this laptop, by the way, and so far have turned up empty on getting the tunre card to work.  I haven't given up yet.  The HP ExpressCard is actually a Hauppage card.  The Hauppage Support page appears to be old when it come to Linux: it mentions Redhat 6.1.  Ouch

---

### Post by sagui on 2007-05-22
> **sambahat said:**
> Are you sure it isn't this device?
Multimedia video controller: Conexant Unknown device 8852 

I have this laptop, by the way, and so far have turned up empty on getting the tunre card to work.  I haven't given up yet.  The HP ExpressCard is actually a Hauppage card.  The Hauppage Support page appears to be old when it come to Linux: it mentions Redhat 6.1.  Ouch

I'm not at all sure which one is which.  It was just an educated guess.

Yeah, I saw that the manufacturer is Hauppage card and I did run into a dead end on their webpage, which for me means that I can't get it to work.  I don't have the skills to write my own drivers, so I rely on the manufacturers.

Well, if you do figure out how to get the thing running please let me know.

---

### Post by Drizzt321 on 2007-08-05
About the Expresscard slot itself. There are no drivers for it. It offers USB2.0 or a 1x PCI-Express slot. For the PCI-Express portion, try using the pciehp or the acpiphp drivers for hotplug support. The first dirver uses the correct PCI-E way of doing things, but not all laptops (in the BIOS) support this because the vender chooses not to for whatever reason. The other way is a different way of doing things, and actually supposedly mimics the XP way.  Read more at this whitepaper from MS about the different methods. Its a good read if you are interested.

[http://www.microsoft.com/whdc/system/bus/pci/BIOS_HotPlugPCIe.mspx](http://www.microsoft.com/whdc/system/bus/pci/BIOS_HotPlugPCIe.mspx)

--Aaron

---

### Post by Tristan Schmelcher on 2007-08-21
I have a Dell XPS M1710 laptop running Debian with similar lspci output. I had to run the following to make the ExpressCard slot work:

```
sudo modprobe pciehp pciehp_force=1
```

After that my own ExpressCard peripheral (an eSATA II adapter from STLab) was recognized.

To make the above happen automatically at boot, add the line "pciehp pciehp_force=1" to /etc/modules.

Best of luck.

(Credit for the solution goes to whoever wrote this: [http://jmaurer.awardspace.info/e8210/](http://jmaurer.awardspace.info/e8210/).)

---

