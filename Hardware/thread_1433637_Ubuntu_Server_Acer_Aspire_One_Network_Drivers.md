---
title: "Ubuntu Server: Acer Aspire One Network Drivers"
date: 2010-03-19
forum: Hardware
---

### Post by mdittmer on 2010-03-19
I recently converted an Acer Aspire One to a tiny server for file backups. The SSD in the laptop had died so I removed it and installed Ubuntu Linux Server 9.10 on a new hard drive inside a USB enclosure.

I ran into some issues installing Linux from the Aspire One, so I ended up plugging the hard drive into another laptop, which I booted using a Ubuntu Linux Sever 9.10 install disk (thumb drive). The installer worked; I was able to select my USB drive partitions for the installations, and I elected NOT to configure the network because I wasn't plugged into the machine where I intended to run Linux.

When I moved the drive back to the Acer Aspire One, everything worked great, except that I had no wired OR wireless drivers loading on boot.

Some quick research seemed to indicate that the r8169 kernel module should work with my wired Ethernet card. However, while running "sudo modprobe r8169" worked (the module is now loaded), I cannot get the Ethernet card working. I tried "sudo ifconfig eth0 up" but got:

eth0: ERROR while getting interface flags: No such device

I tried adding r8169 to /etc/modules and rebooting but ran into the same difficulty.

Any suggestions for getting me a network connection so I can finish setting up the server?

---

### Post by mdittmer on 2010-03-22
Anyone...?

---

### Post by CharlesA on 2010-03-22
Linux installs most drivers by default, so even if you move the install to a different machine it would more then likely work.

What is the output of lspci and lsusb?

---

### Post by mdittmer on 2010-03-22
lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

lsusb:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13fe:1f00 Kingston Technology Company Inc. DataTraveler 2.0 4GB Flash Drive
Bus 001 Device 003: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 002: ID 174c:55aa ASMedia Technology Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by mdittmer on 2010-04-06
This issue seems to be a piece of unavoidable erroneous state from having installed Ubuntu onto a portable hard drive on one machine and then attempting to boot it on another.

I ended up resolving the issue by reinstalling Ubuntu on the machine where the hard drive would be (almost) always connected.

---

