---
title: "Problem with new WD 4TB HDDs"
date: 2014-07-26
forum: Hardware
---

### Post by badger3 on 2014-07-26
Hi All

I have a desktop running 14.04, today I received two new 4TB WD Green HDDs intending to use them in a BTRFS raid1. I've been trying all day to get them working with no success, here's what I've done so far: 

1. I attached the new drives to spare SATA ports and booted. Ubuntu took longer than usual to boot and, when it did, there were no additional sdX devices in /dev 
2. I rebooted into the BIOS and changed the SATA controller to UEFI mode, booted into Ubuntu, still no new devices
3. I checked the BIOS and the new drives are recognised there. 
4. I booted Ubuntu in recovery mode. This shows repeated errors saying "ata3 link is slow to respond"
5. I checked the BIOS version which is at the latest revision (MSI h67ma-e45 mobo)
6. I removed all other SATA devices and booted a live image from USB, still no /dev/sdX devices
7. I plugged the new discs in via a SATA-USB converter, I get a new device in /dev but cannot access the device using fdisk:

> [30104.507237] scsi15 : usb-storage 3-2:1.0[30105.507924] scsi 15:0:0:0: Direct-Access     WDC WD40 EZRX-00SPEB0          PQ: 0 ANSI: 2 CCS
[30105.508986] sd 15:0:0:0: Attached scsi generic sg3 type 0
[30105.510009] sd 15:0:0:0: [sdd] Very big device. Trying to use READ CAPACITY(16).
[30105.510264] sd 15:0:0:0: [sdd] 72057594037927936 512-byte logical blocks: (0 B/0 B)
[30105.510679] sd 15:0:0:0: [sdd] Write Protect is off
[30105.510690] sd 15:0:0:0: [sdd] Mode Sense: 28 00 00 00
[30105.511082] sd 15:0:0:0: [sdd] No Caching mode page found
[30105.511093] sd 15:0:0:0: [sdd] Assuming drive cache: write through
[30105.512254] sd 15:0:0:0: [sdd] Very big device. Trying to use READ CAPACITY(16).
[30105.513115] sd 15:0:0:0: [sdd] No Caching mode page found
[30105.513126] sd 15:0:0:0: [sdd] Assuming drive cache: write through
[30105.513273]  sdd: unknown partition table
[30105.513833] sd 15:0:0:0: [sdd] Very big device. Trying to use READ CAPACITY(16).
[30105.514796] sd 15:0:0:0: [sdd] No Caching mode page found
[30105.514807] sd 15:0:0:0: [sdd] Assuming drive cache: write through
[30105.514816] sd 15:0:0:0: [sdd] Attached SCSI disk
[30141.325923] usb 3-2: USB disconnect, device number 11


I have a WD green 3TB on the same system that works fine on the SATA controller and using the USB SATA adapter. 

8. I tried the USB to SATA adapter in a laptop with the same results. 
9. I've also had the system fail to boot with the new drives in and put me into a shell (UEFI shell?)  

I can't think of anything else to try and I can't get either of the two new discs working:mad:. I presume that both drives may be DOA but that does seem unlikely. Can anyone offer any suggestions? 

Many thanks

---

