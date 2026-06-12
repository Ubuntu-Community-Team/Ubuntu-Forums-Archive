---
title: "Toshiba A200 satellite Bluetooh problem"
date: 2009-07-22
forum: Hardware
---

### Post by topgun_tapan on 2009-07-22
Can anyone guide me how to use Bluetooh on my laptop. After turning the switch on when I run the blutooth manager from my jaunty installation I'm unable to detect any other bluetooth devices nor can the devices detect my blutooth. 

I tried turning bluetooth on but got the following error : $sudo toshset -blutooh on
                                                                                        required kernel toshiba support not enabled.

I tried this after searching for the error and got more errors : $sudo modprobe toshiba_acpi
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.30-020630rc7-generic/kernel/drivers/platform/x86/toshiba_acpi.ko): No such device

Can someone please help me with this ? I really need to run bluetooh.

---

### Post by Shpongle on 2009-07-22
does your laptop have bluetooth built in or do you have an adapter?

---

### Post by topgun_tapan on 2009-07-22
My laptop has bluetooth built in.

---

### Post by topgun_tapan on 2009-07-24
^bump^

---

### Post by davidmohammed on 2009-07-24
try this [thread]("http://ubuntuforums.org/archive/index.php/t-316358.html")

---

### Post by drbin on 2009-07-30
it works. after spending couplaf days searching the web and reading things that users did, I came up with the following. Boot the original vista, enable bluetooth to everything options possible (actually, I believe the trick is done with the service thats looking for BT keyboard and mouse), rebooted vista to make sure that the bt is on. Rebooted to jaunty, BT is there.
Then (to make sure) complete power down, press button to boot and BT was there in jaunty. its magic. still works. spent the time cause I wonna fool around with the bluetooth proximity program. Silly isnt it?

H/W Toshiba Satellite A300-20C with insyde h2o bios 1.9

enjoy.. no patches, no recompilations, just out of the box ubuntu.

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
04:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
04:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
04:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
04:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
04:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0930:0200 Toshiba Corp.         **<----- the built in BT**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

