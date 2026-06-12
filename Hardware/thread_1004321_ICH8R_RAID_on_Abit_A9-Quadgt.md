---
title: "ICH8R RAID on Abit A9-Quadgt"
date: 2008-12-07
forum: Hardware
---

### Post by brad_c6 on 2008-12-07
Hello,
I have a desktop that has three hard drives...

sda (Windows + Linux installed No raid configured)
sdb (Valuable Data RAID1 [Redundancy] labeled "Pic Data" in the BIOS)
sdc (Valuable Data RAID1 [Redundancy] labeled "Pic Data" in the BIOS(2nd Drive)

Ubuntu can see and I assume utilize them, but as seperate drives instead of a RAID. Is there a way to make Ubuntu understand the two HDs as a single drive/RAID Device? The OS is half and half Windows XP Professional (NTFS Format) and half Ubuntu. While the RAID HDs are 650GB {Unfortunatly I can't backup and reiniltize the drives as there is 350GB+ of Data}(Formatted NTFS) that work well in Windows XP as a RAID as the drivers are there and installed.

All support is greatly appreciated :)

---

### Post by oakmac on 2009-01-11
I have a similar setup with the same issue/question.

---

### Post by hotweiss on 2009-01-11
Try installing dmraid:

> sudo apt-get install dmraid

> sudo modprobe dm-raid4-5

---

