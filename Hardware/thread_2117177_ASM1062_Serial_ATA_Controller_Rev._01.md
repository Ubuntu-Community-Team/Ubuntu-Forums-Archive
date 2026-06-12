---
title: "ASM1062 Serial ATA Controller Rev. 01"
date: 2013-02-17
forum: Hardware
---

### Post by MakOwner on 2013-02-17
I have been googling and searching the forums here and I don't see many hits for this controller - it's a SATA III, 6Gb/s two internal and two eSATA ports.  I have the two eSATA enabled - you can only have two of the four ports functioning at once.  

I have it connected to a SANS Digital TR8M enclosure - 8 SATA II disks connected via two quad port SATA III Port multipliers.

I usually go out and get a Silicon Image eSATA controller, or at least one based on the SiL chipset - since SANS digital stareted shipping proprietary HighPoint controllers with non-working drivers.

This time around all I found was this ASMedia controller.  

This ASMedia cards loads and all the drives on it come up before the drives attached to the motherboard come up - so /dev/sda is attached to the ASmedia card instead of the internal controller on the motherboard.

Has anyone else used this controller and have any hints on altering the load order?

---

### Post by Yellow Pasque on 2013-02-17
udev could assign any /sdX to your drives (you can work around it with udev rules), but why do you need consistent drive lettering anyway? That's what UUID is for...

---

### Post by MakOwner on 2013-02-17
> **Temüjin said:**
> udev could assign any /sdX to your drives (you can work around it with udev rules), but why do you need consistent drive lettering anyway? That's what UUID is for...

I'm not worried about the drive lettering -- I think I have a conflict between SATA controllers, and want to change the driver load order to see if the performance issues move.

---

### Post by Yellow Pasque on 2013-02-17
Well, I read your initial post a few more times, but the only issue I see is you're worried about making the drive attached to the mobo /dev/sda
Correct me if I'm wrong :\

---

### Post by Yellow Pasque on 2013-02-17
Oh, and I'm not sure if this is related, but it may be worth trying a kernel >= 3.6 if you're not already: [https://github.com/torvalds/linux/commit/7b4f6ecacb14f384adc1a5a67ad95eb082c02bd1](https://github.com/torvalds/linux/commit/7b4f6ecacb14f384adc1a5a67ad95eb082c02bd1)

---

### Post by MakOwner on 2013-02-17
> **MakOwner said:**
> I'm not worried about the drive lettering -- I think I have a conflict between SATA controllers, and want to change the driver load order to see if the performance issues move.

Hmm...  OK.  
Backstory:


This is on an MSI workstation.  
```

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: NVIDIA Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
04:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
05:00.0 Mass storage controller: Promise Technology, Inc. PDC40718 (SATA 300 TX4) (rev 02)

```

The motherboard has an IDE controller and a 4 port Intel NM10/ICH7 SATA controller in IDE mode.  I have an Promise 4 port PCI SATA controller also - these SATA ports are used for internal drives, all but the boot drive are 2.5" laptop.

I just installed the ASM1062 to connect an external 8 bay enclosure for some work with a bunch of 3.5" desktop drives.

I'm having issues with drive lockups and failures on the drives sitting in the external enclosure behind the ASM1062.

The drives where I have issues work elsewhere; behind the ASM1062 and the port multiplier I get hangs and lockups.

I'm hoping it's just an issue with the controller or a conflict with the other two controllers, otherwise this will be the second brand new 8 bay enclosure I have bought with port multiplier issues.


I have a ticket open with the enclosure vendor, but thought about trying to move things around a bit to eliminate issues on my side of the PMs.

There are some issues with ACPI on this machine with the BIOS, and I see some nasty stuff in dmesg, hence the idea about moving things.

---

