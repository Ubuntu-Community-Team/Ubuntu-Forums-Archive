---
title: "uninstall ubantu and install xp"
date: 2008-07-14
forum: General Help
---

### Post by nimod on 2008-07-14
i hav ubantu on my laptop,i want to delete it and install xp..how can i do?wen i boot from xp cd it shows a error msg that no hardware ie the hardisk is detected..plz help

---

### Post by CautionaryX on 2008-07-14
I would boot the live cd then delete your ubuntu partition using the Partition editor. Then try installing WinXP.

---

### Post by prshah on 2008-07-14
> **nimod said:**
> i hav ubantu on my laptop,i want to delete it and install xp..how can i do?wen i boot from xp cd it shows a error msg that no hardware ie the hardisk is detected..plz help

Should be posted in the Windows forums. Essentially, Windows SATA drivers are not loaded during the installation time. You can temporarily change over to a IDE compatible mode, then, once windows is installed, switch back to a full SATA mode.

Change your BIOS settings for SATA to IDE, Legacy, Compatibility, Native or similar setting. Contact your hardware manufacturer for the exact BIOS setting to change.

---

### Post by LowSky on 2008-07-14
you might need a bootable floppy for sata hard drive to work in a windows install... and people think Windows XP is easier to use...haha

---

### Post by prshah on 2008-07-14
> **LowSky said:**
> you might need a bootable floppy for sata hard drive to work in a windows install... and people think Windows XP is easier to use...haha

This problem affects ubuntu as well; or atleast did till 7.10, I've never tried with 8.04. The install/partitioning program wouldn't see any harddisk drive; fdisk -l would turn up a blank.

---

### Post by Ryadt on 2008-07-14
Go in bios and look for flash module or something like that and disable it. Then go in ata drives, switch from ahci to ata.

---

