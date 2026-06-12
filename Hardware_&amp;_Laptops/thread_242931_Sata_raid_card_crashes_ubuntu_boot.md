---
title: "Sata raid card crashes ubuntu boot"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by bastupungen on 2006-08-24
Hello!
I have a major problem with the PCI sata raid card i am using. I have three Sata disks and the Ubuntu system is installed on one of them, the one connected straight to the motherboard. Installation worked fine, i only had that drive connected. But when i try to add the other two disks (that have a raid1 configuration) into the PCI sata raid card, ubuntu dropps to a shell during boot. Saying it cannot find /dev/sda1 i think. Right at the mounting root file system part of the boot. Everything works fine if i remove the drives from the PCI card, note that the PCI card itself is still in the PCI slot.

I am unsure of what brand the PCI sata raid card is but the chipset is an ALI. I can get the exact nr:s from it, if you need it.

Please help me figure this one out / Jonatan Sandberg Forsgren, Sweden

---

### Post by loney on 2006-08-30
Your BIOS probably sets the PCI slot as the first hard drive if it is available. Check the boot order in the BIOS. Another quick check is the following:

on boot, press escape, press E to edit the GRUB script, change HD0 to HD1, press B to continue boot.

---

