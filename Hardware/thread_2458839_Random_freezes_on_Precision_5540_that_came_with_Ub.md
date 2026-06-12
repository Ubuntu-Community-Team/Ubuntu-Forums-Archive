---
title: "Random freezes on Precision 5540 that came with Ubuntu 18.04"
date: 2021-03-04
forum: Hardware
---

### Post by skathacat0r on 2021-03-04
Had it for under 3 weeks so far but my laptop has locked up over five times now.
It does it randomly, like when starting up (one of the five loading dots orange), or using the touch screen while using Chrome or rotating a view in Blender with just the default cube.
Don't know why it does that or how to reproduce it.
Couldn't find anything in the logs (BIOS, kern.log, syslog).
Still froze once even after reimaging via a USB I created via Dell Recovery.
Once froze during a Skype call, in which the sound was skipping like a CD.

System BIOS has been upgraded to 1.9.1.
Ran Diagnostics (Pre-Boot System Performance Check 4400.13) twice, but with no errors.

I tried chatting with a Live Agent via WhatsApp, but he referred me here because his support is primarily with Windows, and that he assures me that no hardware issues are present as the diagnostics have passed.

Here's the output of `fwupdmgr get-devices`:

```
Precision 5540 Thunderbolt Controller
  DeviceId:             f9296f41259e7d753e918056164777ac2cd49b8e
  Guid:                 42598a87-0ee2-5d7e-b1d1-02a312041fd5 <- TBT-00d40906-native
  Summary:              Unmatched performance for high-speed I/O
  Plugin:               thunderbolt
  Flags:                internal|updatable|require-ac|registered
  Vendor:               Dell
  VendorId:             TBT:0x00D4
  Version:              44.00
  VersionFormat:        pair
  Icon:                 computer
  Created:              2021-03-05


Precision 5540 System Firmware
  DeviceId:             90dce4a3c3eb770c96eaa7fa7f45e984fc66206d
  Guid:                 417d4c2a-87d1-4d7c-bcea-322041f2d5a3
  Plugin:               uefi
  Flags:                internal|updatable|require-ac|supported|registered|needs-reboot
  Version:              0.1.9.1
  VersionLowest:        0.1.9.1
  VersionFormat:        quad
  Icon:                 computer
  Created:              2021-03-05


Precision 5540 TPM 2.0
  DeviceId:             c473de1ae11b072f36cd71aaeac6a445627f4687
  Guid:                 0584e003-d9d2-5b8d-866f-20a2d59bc7ad
  Summary:              Platform TPM device
  Plugin:               uefi
  Flags:                internal|updatable|require-ac|registered|needs-reboot
  Vendor:               Dell Inc.
  Version:              7.2.0.2
  VersionFormat:        quad
  Icon:                 computer
  Created:              2021-03-05


PC711 NVMe SK hynix 512GB
  DeviceId:             f2759da7fe8e0388c5f3601cb072f837b1070b03
  Guid:                 d1294b62-34ff-5b5b-a5c9-7ac4cba4d398 <- STORAGE-DELL-110003
  Guid:                 43971f62-88f2-11ea-bc55-0242ac130003
  Serial:               CN0CN64751260CH2I
  Summary:              NVM Express Solid State Drive
  Plugin:               nvme
  Flags:                internal|updatable|require-ac|registered|needs-reboot|no-auto-instance-ids
  VendorId:             NVME:0x1C5C
  Version:              41001131
  VersionFormat:        plain
  Icon:                 drive-harddisk
  Created:              2021-03-05
```

---

### Post by mikewhatever on 2021-03-05
I wonder how long the "Pre-Boot System Performance Check" takes to run and what is tested.
Random freezes are tricky to diagnose because of too many options. I'd start with a RAM test with memtest. 
It might also help to test with a newer Ubuntu release or a different distro to determine if the problem is with the hardware.

---

### Post by skathacat0r on 2021-03-05
Thanks for your help, but I'm already going to return the laptop.

---

