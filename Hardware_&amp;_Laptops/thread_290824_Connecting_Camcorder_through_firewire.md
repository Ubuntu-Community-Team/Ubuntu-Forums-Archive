---
title: "Connecting Camcorder through firewire"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by hemple on 2006-11-01
i need to transfer video from my camcorder (Mini DV Panasonic PV-GS14) to my laptop. i run dapper drake ubuntu...and i went and bought a firewire cable 4 pin-4 pin. and its connected. but its not picking the camcorder up for some reason. it recognizes my iPod and digital camera automatically though. any suggestions??

not sure if this will help....

lspci....

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 0106: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=AHCI (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0398 (rev a1)
0000:06:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)0000:08:06.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:08:06.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:08:06.2 Mass storage controller: Texas Instruments: Unknown device 803b
0000:08:06.3 0805: Texas Instruments: Unknown device 803c
0000:08:08.0 Ethernet controller: Intel Corporation: Unknown device 1092 (rev 01)


dmesg | tail

[17182468.016000] sdb: assuming drive cache: write through
[17182468.016000] sdb: sdb1
[17182468.588000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17182502.324000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[17182502.324000] ieee1394: Node suspended: ID:BUS[0-00:1023] GUID[00804580d12c930b]
[17182509.016000] ieee1394: Current remote IRM is not 1394a-2000 compliant, resetting...
[17182509.292000] ieee1394: Node resumed: ID:BUS[0-00:1023] GUID[00804580d12c930b]
[17182509.292000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
[17182510.424000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
[17182510.424000] ieee1394: Node suspended: ID:BUS[0-00:1023] GUID[00804580d12c930b]

thanks for your time.

-dan

---

### Post by jtibau on 2006-11-01
i used to have a sony mini dv camcorder and ubuntu 6.06 didn't detect it like it does with the ipod or a digital camera. All I had to do was install kino (video editing software) and from what I remember it came with all the necessary packages for it to work. Then if you want kino to export it to some other formats you have to install ffmpeg.

---

