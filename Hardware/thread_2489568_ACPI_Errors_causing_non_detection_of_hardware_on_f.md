---
title: "ACPI Errors causing non detection of hardware on first boot"
date: 2023-08-03
forum: Hardware
---

### Post by dja440 on 2023-08-03
Hi, i'm fairly new to ubuntu and have recently started getting an error when rebooting and not loading everything connected to a Dell D600 dock. As far as i'm aware the drivers are up to date and this issue presented itself after upgrading to 22.04. 

**System info:**
sudo lsb_release -a
[sudo] password for <hostname>: 
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.2 LTS
Release:	22.04
Codename:	jammy

Grep of dmesg filtering for "ACPI" is attached "acpi.txt" however the culprit (i think) is this line and a few of the lines similar[ATTACH]292559[/ATTACH]

[    4.237483] kernel: ACPI BIOS Error (bug): AE_AML_PACKAGE_LIMIT, Index (0x000000005) is beyond end of object (length 0x5) (20220331/exoparg2-393)
[    4.237526] kernel: ACPI Error: Aborting method \_TZ.GETP due to previous error (AE_AML_PACKAGE_LIMIT) (20220331/psparse-529)
[    4.237537] kernel: ACPI Error: Aborting method \_TZ.CHGZ._CRT due to previous error (AE_AML_PACKAGE_LIMIT) (20220331/psparse-529)
[    4.239101] kernel: ACPI BIOS Error (bug): AE_AML_PACKAGE_LIMIT, Index (0x000000005) is beyond end of object (length 0x5) (20220331/exoparg2-393)
[    4.239138] kernel: ACPI Error: Aborting method \_TZ.GETP due to previous error (AE_AML_PACKAGE_LIMIT) (20220331/psparse-529)
[    4.239148] kernel: ACPI Error: Aborting method \_TZ.CHGZ._CRT due to previous error (AE_AML_PACKAGE_LIMIT) (20220331/psparse-529)
[    4.239162] kernel: ACPI: thermal: [Firmware Bug]: No valid trip found
[    4.244823] kernel: ACPI: thermal: Thermal Zone [PCHZ] (0 C)
[    4.268668] kernel: ACPI: battery: Slot [BAT0] (battery present)
[   11.638228] kernel: ACPI: bus type drm_connector registered
[   14.037111] kernel: ACPI: video: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[   14.048950] kernel: ACPI: video: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   15.060595] kernel: ACPI Warning: \_SB.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20220331/nsarguments-61)

---

