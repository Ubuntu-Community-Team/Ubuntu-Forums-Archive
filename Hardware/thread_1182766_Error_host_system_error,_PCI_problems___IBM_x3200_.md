---
title: "Error: host system error, PCI problems?  / IBM x3200 M2"
date: 2009-06-09
forum: Hardware
---

### Post by josir on 2009-06-09
Hi folks, I have Ubuntu 8.04 installed on a IBM x3200 M2.
Installation worked smoothly and all devices were found and working.

After while, I notice that log is getting bigger and bigger and running dmesg | tail, I got an error that do not stop:

[46776.621648] uhci_hcd 0000:00:1d.2: host system error, PCI problems?
[46776.621651] uhci_hcd 0000:00:1d.2: host controller process error, something bad happened!
[46776.621878] uhci_hcd 0000:00:1d.2: host system error, PCI problems?
[46776.621880] uhci_hcd 0000:00:1d.2: host controller process error, something bad happened!
[46776.622196] uhci_hcd 0000:00:1d.2: host system error, PCI problems?
[46776.622199] uhci_hcd 0000:00:1d.2: host controller process error, something bad happened!

Attached the lspci

josir@linux15:~$ lspci
00:00.0 Host bridge: Intel Corporation 3200/3210 Chipset DRAM Controller (rev 01)
00:01.0 PCI bridge: Intel Corporation 3200/3210 Chipset Host-Primary PCI Express Bridge (rev 01)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5722 Gigabit Ethernet PCI Express
04:03.0 VGA compatible controller: ATI Technologies Inc ES1000 (rev 02)
0c:00.0 SCSI storage controller: LSI Logic / Symbios Logic SAS1064ET PCI-Express Fusion-MPT SAS (rev 02)

How can I fix it or how can I debug this problem?

Thanks in advance,
Josir Gomes

---

