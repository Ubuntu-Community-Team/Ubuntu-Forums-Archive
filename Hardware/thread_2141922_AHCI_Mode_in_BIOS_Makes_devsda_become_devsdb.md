---
title: "AHCI Mode in BIOS Makes /dev/sda become /dev/sdb??"
date: 2013-05-04
forum: Hardware
---

### Post by Singtoh on 2013-05-04
Hello All,

Just curious about this?? As the title says. I have allway installed and run ubuntu in AHCI mode in the BIOS and never noticed anything out of place. But, with this install of Ubuntu 13.04-64bit I have noticed that /dev/sda and /dev/sdb are reversed?? Not only that but during the first install, when in AHCI mode, the installer put the Grub Bootloader on the wrong drive thinking that /dev/sdb was /dev/sda where all previous Ubuntu versions have put the bootloader. I have a Thinkpad T-61 with a 1TB hdd in the ultrabay which has always been /dev/sdb and I have an OCZ ssd in the main bay which has always been /dev/sda. The laptop booted the same with the bootloader on the 1TB drive but it is a bit confusing. Now when I installed this time, I changed the BIOS to Compatibility Mode so the installer sees the drives correctly as OCZ=/dev/sda and 1TB=/dev/sdb. After install things are normal, /dev/sda is OCZ ssd, and /dev/sdb is 1TB hdd, but when I change the BIOS to AHCI mode /dev/sda OCZssd becomes /dev/sdbOCZssd and /dev/sdb 1TBhdd becomes /dev/sda 1TBhdd and the disk utility and everywhere else reports the same. Changing back to Compatibility Mode makes things "write" again, but I have always read that for performance sake you should always run in AHCI Mode??. Like I said it is a bit confusing. Could someone please tell me if this is a bug??, or if there is something in fstab or somewhere that I can change to make things rite again??? Thanks in advance for any insight on this issue.

Cheers,

Singtoh

---

