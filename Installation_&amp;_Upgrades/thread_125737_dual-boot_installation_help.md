---
title: "dual-boot installation help"
date: 2006-02-04
forum: Installation &amp; Upgrades
---

### Post by maxxag on 2006-02-04
ok, ive decided to ditch my buggy raid array that my windows install is on, and switch to a setup that consists of one 120gb HDD with windows, one 80gb HDD with ubuntu, and one 120gb HDD as a kind of general file repository/transfer area for both OS's to share, which would be formatted as FAT32.  So, my question is, to go from RAID0 on the two 120's to a master/slave on them, what do i have to do?  the RAID0 itself is hardware based from my mobo (an asus with an onboard VIA RAID controller), and ive figured that i can delete the RAID array setup from before grub pops up in the boot sequence, but do i have to do anything beyond that to set up the drives (jumpering, etc)?  and after ive got the drives set-up, should i install XP first then install ubuntu and let grub overwrite the windows bootloader?  and lastly, how to i format the slave drive to be FAT32 instead of NTFS from windows?  can i do it directly from the OS or during the windows installation?

EDIT: i forgot to say, the two 120gb HDD's are SATA and the 80gb one is IDE, if that makes any difference

well, thanks for helping a newb such as myself, i appreciate any advice you guys can give me!

---

