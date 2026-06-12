---
title: "No sound with Sound Blaster X-Fi Elite Pro installed"
date: 2011-06-02
forum: Hardware
---

### Post by DreadWolf on 2011-06-02
Hello everyone who is reading this,

Ok here is the situation... I'm using a GETAC M230 laptop and I have installed a Sound Blaster X-Fi Elite Pro PIC card in it (well it's not installed inside the laptop but it's installed in a Magma PCI 4 slot expansion bay with a CBHIF interface to the laptop) I'm also using Ubuntu 10.10 (notebook edition) as the OS for the laptop. I know the hardware is working fine and that the OS see's the hardware nicely because of this...

```

dreadtech@Dread-M230:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M G] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
04:06.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
04:0a.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
04:0a.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
06:00.0 PCI bridge: Hint Corp HiNT HB4 PCI-PCI Bridge (PCI6150) (rev 04)
07:04.0 PCI bridge: Pericom Semiconductor PCI to PCI Bridge (rev 02)
08:04.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
08:04.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
08:04.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
[COLOR="Red"]08:05.0 Multimedia audio controller: Creative Labs SB X-Fi[/COLOR]
08:06.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)
08:07.0 Mass storage controller: Promise Technology, Inc. PDC40718 (SATA 300 TX4) (rev 02)

```

```

dreadtech@Dread-M230:~$ lspci | grep audio
08:05.0 Multimedia [COLOR="Red"]audio[/COLOR] controller: Creative Labs SB X-Fi

```

After doing hours of searing, I see many other people had similar situations and have got them fix by downloading all kinds of drivers and compiling them but after following other examples, I still cannot get my card working. The software just doesn't want to play nice it seems lol.

Is there anyone that could please help me with this situation? :(

---

