---
title: "Targus Card reader/Writer"
date: 2008-09-29
forum: Hardware
---

### Post by Mr.Bazerkus on 2008-09-29
I bought this Media card reader(sd,sdhc,mmc) for Ubuntu expecting it to work right out of the box. When I plugged it in nothing happen ubuntu had no signs of recognizing the cards I use my xp computer and it still work. If anyone could help me figure out why its not working in Ubuntu that would be appreciated I enter this command  Ispci not sure what it does but I will add it just in case it helps I have a ubuntu hardy with all the latest updates. > 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
02:0e.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)


---

### Post by Alderin on 2009-03-28
I'm having the same problem, this is a 'bump'.  Slightly different device, I believe, because my Targus device also has Compact Flash, which is what I bought it for.

Syslog:
```

Mar 28 09:02:40 alderin-laptop kernel: [53374.768089] usb 5-3: new high speed USB device using ehci_hcd and address 6
Mar 28 09:02:41 alderin-laptop kernel: [53374.919384] usb 5-3: configuration #1 chosen from 1 choice
Mar 28 09:02:41 alderin-laptop kernel: [53374.965721] scsi6 : SCSI emulation for USB Mass Storage devices
Mar 28 09:02:41 alderin-laptop kernel: [53374.987142] usb-storage: device found at 6
Mar 28 09:02:41 alderin-laptop kernel: [53374.987153] usb-storage: waiting for device to settle before scanning
Mar 28 09:02:46 alderin-laptop kernel: [53379.985344] usb-storage: device scan complete
Mar 28 09:02:46 alderin-laptop kernel: [53380.004494] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
Mar 28 09:02:46 alderin-laptop kernel: [53380.781372] sd 6:0:0:0: [sdb] 3915072 512-byte hardware sectors (2005 MB)
Mar 28 09:02:46 alderin-laptop kernel: [53380.782106] sd 6:0:0:0: [sdb] Write Protect is off
Mar 28 09:02:46 alderin-laptop kernel: [53380.782116] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
Mar 28 09:02:46 alderin-laptop kernel: [53380.782122] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Mar 28 09:02:46 alderin-laptop kernel: [53380.785739] sd 6:0:0:0: [sdb] 3915072 512-byte hardware sectors (2005 MB)
Mar 28 09:02:46 alderin-laptop kernel: [53380.786480] sd 6:0:0:0: [sdb] Write Protect is off
Mar 28 09:02:46 alderin-laptop kernel: [53380.786486] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
Mar 28 09:02:46 alderin-laptop kernel: [53380.786491] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Mar 28 09:02:46 alderin-laptop kernel: [53380.786502]  sdb: sdb1
Mar 28 09:02:46 alderin-laptop kernel: [53380.787487] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Mar 28 09:02:46 alderin-laptop kernel: [53380.787724] sd 6:0:0:0: Attached scsi generic sg2 type 0

```

Then a manual attempt to mount:
```

# mount -t vfat /dev/sdb1 /media/cardreader
Mar 28 09:10:46 alderin-laptop kernel: [53860.284067] FAT: count of clusters too big (488768)
Mar 28 09:10:46 alderin-laptop kernel: [53860.284080] VFS: Can't find a valid FAT filesystem on dev sdb1.

```

I'm a bit confused.  fdisk shows one partition on /dev/sdb listed as FAT16.  I tried both -t vfat and -t msdos with the same results.  It is a 2gb compact flash card, and the device worked before with this hardware when running XP, and still works with other systems.

Other than that and my GPS I've been totally impressed with Ubuntu's grasp of my laptop's hardware!

Thanks for the help!

---

### Post by Chemical Imbalance on 2009-03-28
I think the cable that came with my Targus reader is defective because I also had this problem until I swapped it with my usb-harddrive cable.

---

### Post by Alderin on 2009-03-30
Not the problem on my end, since the same cable works in another machine (running windoze), and the USB port works with my thumbdrives just fine.  A cable issue wouldn't likely allow the Kernel to detect and seemingly fully connect with the device.

---

### Post by Chemical Imbalance on 2009-03-30
I'll look up my output of lsusb later with that cable, but I know it was receiving power.  It also was not a usb-port issue as I tried it on several computers.  Its probably not worth the shipping costs for any warranty on it for me though.

---

### Post by Alderin on 2009-05-27
I have updated to Ubuntu 9.04 (Jaunty), but still cannot read from my cardreader.  Interesting note, though: I re-installed Windows XP MCE in a virtual machine using Sun's Virtualbox, and gave the virtual Windows access to the USB port, and Windows CAN read the device.

So, no, it isn't a hardware thing.

---

### Post by Chemical Imbalance on 2009-05-29
Interesting.  I don't know if I've tried mine in Windows.

I'll give that a try sometime.  Though I think mine is a hardware problem.

---

### Post by darkorical on 2009-06-02
I have a Targus USB DVD ROM (PACMB010U) and when  I attach it to Ubuntu 9.04 it also shows no signs what-so-ever of being recognized 

(bummer on trying to install Sims 3 on release night)

---

