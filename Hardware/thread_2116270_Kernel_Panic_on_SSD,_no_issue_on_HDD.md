---
title: "Kernel Panic on SSD, no issue on HDD"
date: 2013-02-15
forum: Hardware
---

### Post by voided3 on 2013-02-15
I am running Lubuntu 12.10 on an HP DV4-2165dx laptop with a 2.13ghz Intel i3 dual core and 8GB DDR3 running the latest BIOS. When I am running a fresh install of Lubuntu 12.10 on a Seagate 5400rpm 250GB SATA drive, it runs like a top; no issues. When I use it with a G. Skill Phoenix SATA III 120GB SSD and an equally fresh install of Lubuntu 12.10, it installs the OS just fine and it runs completely normally, even after doing a few reboots. However, I get fairly consistent kernel panics on a cold boot with the caps lock light blinking only when using the SSD. Is my SSD too fast for my I/O controller or is there a known issue with the kernel? I had Linux Mint 14 installed on the SSD that I upgraded the kernel to 3.7.7 with and it, too, showed the same symptoms. Any suggestions? Thank you in advance!

---

### Post by voided3 on 2013-02-16
Well, I searched a bit more and tried a few things. I added "libata.force=noncq" to my GRUB configuration file and disabled the splash screen, but I still get a kernel panic on a cold boot. Should I just go back to the slow 5400rpm Seagate and save this SSD for a newer machine, or are there any other tricks?

---

