---
title: "New mobo sata problem"
date: 2009-01-23
forum: Hardware
---

### Post by thejem on 2009-01-23
I recently had a mobo crash and bought a new GeForce 8200 mobo. I had Win XP and Vista running on a Sata drive and Ubuntu 8.10 running on an ata drive. Changed mobos and left bios at defaults and both windoz ran fine even before using mfg disk to update drivers. Ubuntu will not see my sata drive and will not boot properly from ata drive because the boot sector has changed order. My sata in the bios is set up as sata and I changes it to ACPI? or whatever and tried the raid setting. Neither one made the sata available to Ubuntu. The also made windos crash while loading. Went back to sata mode and windos worked fine again. Guess I'll have to giv up Ubuntu until thsi problem is solved. Like I said it worked fine with the old mobmo.
:(

---

### Post by cariboo on 2009-01-23
If your BIOS has an AHCI setting, give that a try, Windows XP may not boot, unless it is fully updated, but VIsta shouldn't have a problem. I run the same sort of setup, but I have Windows 7 and Intrepid on a PATA drive and Jaunty on a SATA drive. If you have a problem with device_lables changing, use uuid instead. Here is an example of my /boot/grub/menu.lst from my Interpid install:

```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		da96f95c-3bbb-47f2-8b4e-d27168650688
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=da96f95c-3bbb-47f2-8b4e-d27168650688 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
```

Jim

---

### Post by thejem on 2009-01-25
Nope no luck. Set bios to AHCI and still no SATA drives listed in Ubuntu.
Tried downloading the latest version of Suse too and she doesn't see them either. Must be something about the chipset for sata that the kernal doesn't recognise.

---

### Post by thejem on 2009-01-25
Tried everything and linux will not recognize my sata drives. The bios has three settings for sata: SATA, RAID, AHCI. Tried ll three. Nothing.
Chosing AHCI adds a setting: "Change the AHCI DID for Linux---Enable-Disable.
Tried both ways. Nothing. There is another setting for SATA in the bios that has two options -- Disabled or Linear down. Tried both with all other settings and still nothing. Guess I'll just have to wait until  another kernal update and go back to ms in the meantime. 
:(:(:(

---

