---
title: "Pavilion dv8000 driver help"
date: 2010-06-01
forum: Hardware
---

### Post by p0l1wrath on 2010-06-01
i need all the drivers for linux for a hp pavilion dv8000 i cant find them anyway having trouble booting windows on it so 100% ubuntu :)
i mostly need the graphics card driver but all others as well:D
cheers for any help in advance :)

---

### Post by Yellow Pasque on 2010-06-01
AFAICT, it's an ATI Xpress 200, so the graphics card driver is pre-installed. Ideally, all of the drivers are pre-installed from the kernel, so if something isn't working, you need to be more specific. At least give the output of:
```
lscpi
```

---

### Post by p0l1wrath on 2010-06-02
very sorry but im quite new to linux and stuff all i know is i can run 3d effects and when i go fullscreen on 4od it goes all blotchey i dunno what "lscpi" is?
soz

---

### Post by p0l1wrath on 2010-06-02
sorry found out what it was :)

oli@oli-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
08:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by cascade9 on 2010-06-02
The video card is a GeForce Go 7400. 

To get the drivers for it, the easiest way is to go to

System-> Administration-> Hardware Drivers 

You might (not sure on this) need drivers for the 5-in-1 Multimedia Card Reader, the IEEE 1394 Host Controller (firewire) but I dont think you will. 

Everything else should work out of the box ;)

---

### Post by SurferEddie on 2010-07-20
I'm new to Ubuntu as well and have a DV8000.  Did you load the desktop or the netbook?  Also, where can I get all the drivers.  Thank

---

### Post by p0l1wrath on 2010-07-20
i loaded the notebook and read the reply above;)

---

