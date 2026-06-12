---
title: "can not install linux"
date: 2008-09-19
forum: General Help
---

### Post by user11 on 2008-09-19
I am trying to install Ubuntu 8.04.1 in my new system build:

Western Digital VelociRaptor WD1500HLFS 150GB 10000 RPM SATA 3.0Gb/s Hard Drive

Pioneer 20X DVD±R DVD Burner Beige SATA Model DVR-215D

AMD Athlon X2 5400B 2.8GHz Socket AM2 65W Dual-Core Processor Model ADO540BDOBOX

Kingston 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model KVR800D2N5K2/4G

EVGA 512-P3-N841-AR GeForce 8800GTS (G92) 512MB 256-bit GDDR3 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card

ASUS M3N78-EMH HDMI AM2+/AM2 NVIDIA GeForce 8200 HDMI Micro ATX AMD Motherboard

The problem is that it doesn't boot and it just goes to some Busy-box selection screen (samething with Xubuntu). When I tried ubuntu 7.10, the monitor just turns off instead of booting, and in puppy 4.00 i get some tty error. All live CDs are fine as they work in other systems. Performing a bios update did nothing.:confused:

Any help is appreciated.:(

---

### Post by mbeach on 2008-09-19
just a guess, but have you tried the alternate cd instead of the live cd.  Browse to:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
and select the checkbox under the Start Download button for the alternate cd.

its gotton through a few installs for me that didn't work with the live cd.

---

### Post by mb_webguy on 2008-09-19
I've had problems installing both Linux and Windows to SATA hard drives before, and I've found that it sometimes helps to change the SATA mode in the system BIOS.  Usually you're given the option of AHCI or RAID, and changing it from the current setting to the other and then reinstalling the OS sometimes works.

Ad as mbeach said, sometimes the alternate install disc will work when the LiveCD won't.

---

