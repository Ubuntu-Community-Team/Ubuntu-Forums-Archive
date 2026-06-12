---
title: "Santa Rosa Macbook Pros"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by xpaulbettsx on 2007-06-15
Starting a thread to collect information about the new MBP's with Santa Rosa chipset. Currently, these are pretty glitchy under even Gutsy, so here's some info. 

**Output of lspci**
```

00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation Mobile SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0407 (rev a1)
0b:00.0 Network controller: Atheros Communications, Inc. Unknown device 0024 (rev 01)
0c:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 436a (rev 13)
0d:03.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02)

```

There was already a bug on the HAL mailing lists regarding the MBP having a different model name that isn't picked up by the backlight - I think this will be fixed in Git though.

---

### Post by xpaulbettsx on 2007-06-15
Here's the current list of problems, as I experience from Gutsy kernel (probably isn't complete, here's what I've found):

[LIST]
[*]Newest nVidia driver doesn't work - screen goes black, turns off blacklight - I need to see if the machine is completely hung or you can get in over SSH
[*]Backlight dimming doesn't work (fixed in HAL Git)
[*]CD-ROM doesn't show up as a device node, I saw something in dmesg but I haven't tracked it down yet
[/LIST]

---

### Post by saserlite on 2007-06-24
Similar thread here: [http://ubuntuforums.org/showthread.php?t=474144]("http://ubuntuforums.org/showthread.php?t=474144").

---

