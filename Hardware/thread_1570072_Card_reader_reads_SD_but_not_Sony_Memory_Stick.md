---
title: "Card reader reads SD but not Sony Memory Stick"
date: 2010-09-07
forum: Hardware
---

### Post by davewilkinson on 2010-09-07
I have a Toshiba Equium laptop (P300-190) that i have installed ubuntu 10.04 on. All hardware seems to work perfectly which is great apart from the internal multi card reader, which partially works.

SD cards are read and mounted no problem but when i use a sony memory stick they are not recognised, The reader is made my o2 micro inc and there appears to be no drivers available on their website for any platform.

So far i have used 2 sony memory sticks, both of which do not work. They had both previously worked under vista and windows 7 so i know there is not a hardware fault. I have formatted the memory sticks in a sony digital camera which has not worked. I have also started the laptop with the card inserted but still no joy.

Both the cards are in fact the smaller memory stick duo's which are being used in a memory stick adapter if this makes any difference? again both of these worked in windows using the adapter.

As a work around i can import pictures using the cameras USB cable but i would ideally like to get the card reader working.

below is the output from lspci.

I hope someone can help.

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

---

### Post by Fafler on 2010-09-07
I think it's because of a incomplete drivers. I know it was, back when i had a laptop with a similar cardreader. Something about the DRM used in Memory sticks not being supported.

You could search for another driver, but often it takes quite a bit of skill to install such things correctly.

---

### Post by davewilkinson on 2010-09-07
thanks for the respnse.

so basically i just have to get used to not being able to use the card reader with sony memory sticks?

---

