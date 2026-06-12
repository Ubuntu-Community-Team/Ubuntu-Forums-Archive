---
title: "SD Card reader"
date: 2006-10-05
forum: Hardware &amp; Laptops
---

### Post by bon_bkdfighter on 2006-10-05
Hi,

I'm trying to get the built in card reader for my toshiba m40/m45 laptop. I have ubuntu dapper drake and here's the output I get when I type: "lspci"

0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
0000:00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
0000:00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
0000:00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
0000:00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
0000:01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 Fast Ethernet Controller (rev 10)
0000:05:04.0 Network controller: Intel Corporation PRO/Wireless 2915ABG MiniPCI Adapter (rev 05)
0000:05:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
0000:05:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
0000:05:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
0000:05:06.4 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller

I also tried "dmesg | tail" after inserting a 2 gb sd card into the slog and get some errors like this:
[17188389.628000] mmcblk0: error 2 transferring data
[17188389.628000] end_request: I/O error, dev mmcblk0, sector 0
[17188389.628000] mmcblk0: error 2 transferring data
[17188389.628000] end_request: I/O error, dev mmcblk0, sector 0
[17188389.632000] mmcblk0: error 2 transferring data
[17188389.632000] end_request: I/O error, dev mmcblk0, sector 0
[17188389.632000] mmcblk0: error 2 transferring data
[17188389.632000] end_request: I/O error, dev mmcblk0, sector 0
[17188389.632000] mmcblk0: error 2 transferring data
[17188389.632000] end_request: I/O error, dev mmcblk0, sector 0

Here's what I get after inserting the sd card and typing "dmesg | grep hd"
[17179573.268000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17179573.276000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[17186063.680000] SCSI device sdb: 4019200 512-byte hdwr sectors (2058 MB)
[17186063.688000] SCSI device sdb: 4019200 512-byte hdwr sectors (2058 MB)

thanks in advance. any help would be appreciated.
Bon.

---

### Post by InsanityLivz on 2007-09-16
This works for me using deb. should work for you.

1. Log into Root Terminal

2. Type 

cd /etc
pico rc.local

3. add this line after the commented out section (# = comment) but before exit0

setpci -s 06.3 4c=0x22

exit, save, rebewt, voila.

---

