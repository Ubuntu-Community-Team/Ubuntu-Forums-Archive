---
title: "8gb MicroSD not recognized on S10-2"
date: 2010-01-25
forum: Hardware
---

### Post by sameersegal on 2010-01-25
Hi,

I have a strange problem and I can't figure out a solution. The solution for Acer netbooks on Filthy Pants doesn't work for me.

Computer: S10-2 | Ubuntu 9.04 UNR.

A 2GB SD card gets mounted automatically but an 8GB microSD doesn't even appear as a device node - no /dev/sdb or /dev/sde

[PHP]myslate@myslate-v1:~$ tail -f /var/log/messages
Jan 25 19:30:05 myslate-v1 kernel: [  877.930809] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
Jan 25 19:30:05 myslate-v1 kernel: [  878.657298] sd 6:0:0:0: [sdb] 15523840 512-byte hardware sectors: (7.94 GB/7.40 GiB)
Jan 25 19:30:05 myslate-v1 kernel: [  878.658157] sd 6:0:0:0: [sdb] Write Protect is off
Jan 25 19:30:05 myslate-v1 kernel: [  878.664168] sd 6:0:0:0: [sdb] 15523840 512-byte hardware sectors: (7.94 GB/7.40 GiB)
Jan 25 19:30:05 myslate-v1 kernel: [  878.665028] sd 6:0:0:0: [sdb] Write Protect is off
Jan 25 19:30:05 myslate-v1 kernel: [  878.665073]  sdb: sdb1
Jan 25 19:30:05 myslate-v1 kernel: [  878.667803] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Jan 25 19:30:05 myslate-v1 kernel: [  878.673684] sd 6:0:0:0: Attached scsi generic sg1 type 0
Jan 25 19:30:24 myslate-v1 kernel: [  897.558892] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 25 19:30:24 myslate-v1 kernel: [  897.558910] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information
Jan 25 19:30:43 myslate-v1 kernel: [  916.202770] sd 6:0:0:0: [sdb] Sense Key : No Sense [current] 
Jan 25 19:30:43 myslate-v1 kernel: [  916.202789] sd 6:0:0:0: [sdb] Add. Sense: No additional sense information[/PHP]

This might be of additional help.

[PHP]
yslate@myslate-v1:~$ lspci
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
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
myslate@myslate-v1:~$ 
[/PHP]

I will really appreciate any help regarding this.Thanks

Sameer

---

