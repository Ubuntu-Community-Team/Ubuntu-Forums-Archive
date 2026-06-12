---
title: "dock Dell TB16 does not work with XPS 13"
date: 2019-11-12
forum: Hardware
---

### Post by Gingalone on 2019-11-12
I have just bought a dock Dell TB16 to connect to my laptop Dell XPS13 9370; dock installing instructions recommend to update BIOS and drivers before to connect the dock to the laptop but on [www.dell.com](www.dell.com) there are no drivers for Ubuntu and only a Windows file(!) (XPS_9370_1.11.1.exe) for BIOS update... 
I tried to connect the dock anyway but nothing works, no mouse, no keyboard, no wired network...
Any suggestion? Did anyone get this problem?
Thank you for help.

---

### Post by oldfred on 2019-11-12
Dell now supports UEFI updates from within Ubuntu/Linux.
[https://fwupd.org/lvfs/devices/](https://fwupd.org/lvfs/devices/)
I see this on the list:
TB16 VMM3320 MST Device Update

[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
sudo fwupdmgr get-devices
sudo fwupdmgr get-updates

---

### Post by Gingalone on 2019-11-13
Thank you oldfred, it looks the possible solution involves a "digital" knowledge rather deeper than available (mine!): I don't know what to do with the .cab file provided by Dell (in LVFS site) and what the two commands you suggested do...
I even don't know is my laptop has BIOS or UEFI (how can I see that?) recentely I updated the BIOS though a file provided by Dell in its website where they call it BIOS...
I would need a guide step by step...

---

### Post by oldfred on 2019-11-13
Many companies still call it BIOS, but it has been UEFI since 2012. Microsoft required UEFI with gpt partitioning starting with Windows 8 in 2012.

I do not have a newer Dell, but thought this is all you have to do:

sudo fwupdmgr get-devices
sudo fwupdmgr get-updates

---

### Post by Gingalone on 2019-11-15
I'll try the two commands you suggested oldfred, does the dock need to be connected?

---

### Post by oldfred on 2019-11-15
I would think dock would need to be connected, so it can see it. Not sure how that works with added devices.

---

### Post by Gingalone on 2019-11-18
I did what you recommended oldfred:```
sudo fwupdmgr get-devices
sudo fwupdmgr get-updates 
``` (I can add the output of the commands if needed) anyway it looks all went well but, alas, the dock still does not work...

---

### Post by oldfred on 2019-11-18
Did it show when you got devices your dock, so it was on list to be updated?

---

### Post by Gingalone on 2019-11-20
Thank you oldfred for the assistance; this is what I got from your suggested commands (done with the dock connected):```
XPS-13-9370:~$ sudo fwupdmgr get-devices
[sudo] password for gingus: 
XPS 13 9370 Thunderbolt Controller
  DeviceId:             798df3df54f1b1b43fc0e9769c50c03255a9fda4
  Guid:                 4eeb9d07-a96c-56d6-92d3-4a23ee7a6e4a <- TBT-00d407e6
  Summary:              Unmatched performance for high-speed I/O
  Plugin:               thunderbolt
  Flags:                internal|updatable|registered
  Vendor:               Dell
  VendorId:             TBT:0x00D4
  Version:              33.00
  Icon:                 computer
  Created:              2019-11-20

Dell Thunderbolt Cable
  DeviceId:             ffd20a9e0ee77fe2197c7de5aa7856fb4c886c1e
  Guid:                 b4fd3cdf-4e3a-5090-a583-45367cfd6421 <- TBT-00d4b051
  Plugin:               thunderbolt
  Flags:                updatable|registered
  Vendor:               Dell
  VendorId:             TBT:0x00D4
  Version:              16.00
  Icon:                 audio-card
  Created:              2019-11-20

Dell Thunderbolt Dock
  DeviceId:             cfa51b7ee2e9da6f96f618c66aba87b185f1c11e
  Guid:                 76cc74d4-f062-5b93-a11c-8d2a58a25848 <- TBT-00d4b054
  Plugin:               thunderbolt
  Flags:                updatable|registered
  Vendor:               Dell
  VendorId:             TBT:0x00D4
  Version:              27.00
  Icon:                 audio-card
  Created:              2019-11-20

XPS 13 9370 System Firmware
  DeviceId:             8a21cacfb0a8d2b30c5ee9290eb71db021619f8b
  Guid:                 7ceaf7a8-0611-4480-9e30-64d8de420c7c
  Plugin:               uefi
  Flags:                internal|updatable|require-ac|supported|registered|needs-reboot
  Version:              0.1.11.1
  VersionLowest:        0.1.11.1
  Icon:                 computer
  Created:              2019-11-20

KXG60ZNV512G NVMe TOSHIBA 512GB
  DeviceId:             f954c7acdf5fab61aeaca1cd71d29ea5ade6992f
  Guid:                 8a412b95-5c07-5ce4-b63a-f9cbf254dd5d <- STORAGE-DELL-107443
  Guid:                 344c2804-4948-e811-842f-0ed5f89f718b
  Serial:               Z83A20RJK02N
  Summary:              NVM Express Solid State Drive
  Plugin:               nvme
  Flags:                internal|updatable|require-ac|registered|needs-reboot|no-auto-instance-ids
  Vendor:               Toshiba America Info Systems
  VendorId:             NVME:0x1179
  Version:              10604103
  Icon:                 drive-harddisk
  Created:              2019-11-20

gingus@gingus-XPS-13-9370:~$ sudo fwupdmgr get-updates
No upgrades for XPS 13 9370 System Firmware, current is 0.1.11.1: 0.1.11.1=same, 0.1.10.0=older, 0.1.9.0=older, 0.1.8.1=older, 0.1.6.3=older
gingus@gingus-XPS-13-9370:~$ 
 
```Still the dock does not work (a part from the external display)

---

### Post by oldfred on 2019-11-20
The update definitely recognized your dock.
But it did not do an update, but it looks like version is very current, by created date.
Shows it needs reboot.
Not sure then if that is a warm reboot or a full cold shutdown, remove all power, hold power switch to drain all power & then reboot, so system updates its hardware list. I would do that with dock plugged in.

Not sure what else to suggest.

---

### Post by Gingalone on 2019-11-25
I did the "full cold shutdown" as you suggested oldfred and now it works! I had to "unlock" Thunderbolt device in the system settings and get both Dell Thunderbolt Dock and Dell Thunderbolt Cable "Authorized".
Now mouse, keyboard, external monitor work, only the wired ethernet connection looks not very stable (wireless is OK)...
Anyway a huge improvement, thank you oldfred!

---

### Post by oldfred on 2019-12-16
Settings in UEFI required for Thunderbolt.
       [https://ubuntuforums.org/showthread.php?t=2433026](https://ubuntuforums.org/showthread.php?t=2433026)
[https://askubuntu.com/questions/1195666/dell-wd19tb-thunderbolt-dock-failed-to-authorize-device/1196574#1196574](https://askubuntu.com/questions/1195666/dell-wd19tb-thunderbolt-dock-failed-to-authorize-device/1196574#1196574)

---

