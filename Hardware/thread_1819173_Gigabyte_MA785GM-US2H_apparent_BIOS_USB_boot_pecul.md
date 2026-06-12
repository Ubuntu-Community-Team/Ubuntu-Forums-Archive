---
title: "Gigabyte MA785GM-US2H apparent BIOS USB boot peculiarity"
date: 2011-08-05
forum: Hardware
---

### Post by walt.smith1960 on 2011-08-05
I've been frustrated with trying to get my desktop with the above motherboard to boot Ubuntu installed to a USB stick.  I'd create a stick using either Startup Disk Creator or Unetbootin. The USB drive would work fine with an older Gigabyte MoBo (GM74) or in a Thinkpad. The AMD785 desktop would show either "boot error" or "grub rescue".  I updated the BIOS to the latest and no help.

It appears that the Award BIOS uses some sort of Microsoft code.  I was reading about this problem in some forum or other and formatting  the USB drive in Windows was suggested.  When I formatted the flash drive in Win 7 and created a Mint 11 Live USB, it boots reliably.  Apparently there's something placed in the FAT32 file system by Windows that isn't installed when formatting with Gparted.  Gigabyte's  BIOS need that something to boot.  Just a heads-up for Gigabyte or AMD785 chipset MoBo users.

---

