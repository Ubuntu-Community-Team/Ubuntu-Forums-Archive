---
title: "Cant install XP on UBUNTU 9.04"
date: 2009-04-25
forum: Hardware
---

### Post by nexoncore on 2009-04-25
I recently formatted my hard drive and made 3 partitions, 1 for ubuntu as my primary os, one as swapspace and one formatted to ntfs for windows xp to be installed on.

Problem is, since ubuntu and grub have been installed, the windows xp cd has decided it can not detect my hard drive, hence I cant install it.

Does anyone know how I can fix this little issue?

---

### Post by cariboo on 2009-04-26
If you have AHCI enabled in your BIOS, windows won't see your hard drive. If you have a driver floppy for XP you can install at the start of the installation when it says press F6 to install drivers. You could also turn off AHCI, and you should be able to install windows.

---

### Post by nexoncore on 2009-06-16
Sorry for the late reply, thanks for your advice. I found it was because my laptop was using a Sata HDD, so I downloaded a SATA modified XP iso and sorted it out

---

