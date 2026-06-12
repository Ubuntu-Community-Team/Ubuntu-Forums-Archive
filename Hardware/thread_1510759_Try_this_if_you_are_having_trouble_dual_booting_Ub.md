---
title: "Try this if you are having trouble dual booting Ubuntu and WIndows"
date: 2010-06-15
forum: Hardware
---

### Post by izz.y on 2010-06-15
Hello World,
I was initially having a lot of trouble triple booting Ubuntu 10.04 64-bit, windows XP 32-bit, and Windows 7 64-bit. I had installed both Windows in one hard drive, and Ubuntu in my other hard drive. Both hard drives were SATA. I have an ASUS M4A78L-M motherboard, and in the BIOS I can set the hard drives to use IDE, AHCI, or RAID. If I used AHCI, Ubuntu would boot, but Windows 7 would reboot immediately, and XP would blue screen, but if I used IDE, Ubuntu would boot to a black screen, but both XP and 7 would work flawlessly. GRUB 2 worked in either setting. I was about to ask for help, but then I realized I could set each drives mode independently. I set the drive with windows on it to use IDE, and the drive with Ubuntu on it to use AHCI, and sure enough it worked flawlessly. IF anyone else has this problem, I hope they find the solution. If anyone wants to know more about my hardware, just post on this thread, and I will try to reply soon.

---

