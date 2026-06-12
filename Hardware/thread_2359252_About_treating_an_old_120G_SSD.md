---
title: "About treating an old 120G SSD"
date: 2017-04-21
forum: Hardware
---

### Post by satimis on 2017-04-21
Hi all,

Daily working computer
CPU - AMD 8-core
RAM - 32G
HD - 1TB SSD

Spare computer
CPU - AMD 8-core
RAM - 8G
HDs - 120G SSD for OS
          1.5TB WD Black Label HD for storage

I have 2 old 120G SSD.  One is used in a spare computer for installing OS-Ubuntu 16.04 with 1.5TB WD Black Label for storage.  Another old 120G SSD is connected in the daily working computer for standby only.

Would it be possible to combined these 2 120G SSD in the spare computer, as an 240G SSD for installing OS?  If possible please advise how?

Thanks in advance.

Regards
satimis

---

### Post by paulisdead on 2017-04-21
You could either use them in a RAID0 array or LVM them together.  The ubuntu installer has options to set up a software MDADM array, so that'd be pretty easy.  I haven't looked too closely at the LVM options in the installer, but it probably has options to combine them into a logical volume.  **Be aware, if one drive dies in either configuration, you could lose all the data.**  Might as well just do raid0 and get the speedup, unless you think you might want to add more volumes in the future.

Just google smack ubuntu software raid or mdadm and you should find a ton of info.  Might also want to read up on different RAID levels, for what you describe you probably want 0.

---

