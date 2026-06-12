---
title: "Jaunty will no longer recognize fat32 raid, how do I get it back?"
date: 2009-09-30
forum: Hardware
---

### Post by thirdrev on 2009-09-30
I am currently running Jaunty on an IDE with windows on a SATA Raid1 (the fake on-board kind). I had to install Intrepid with the alternate install CD to get it to properly recognise and address the RAID (instead of addressing it as two separate disks which caused its own set of problems). However, Ubuntu did recognise the disks even before the alternate install. I even wrote a little script to automatically mount the raid. 

Now that I have "upgraded" to jaunty: The RAID is not recognised either as a raid or independent disks - nothing, nada. Furthermore, the windows option on grub throws and error at me. I know the raid is still good though, because when I change the boot order in the bios and boot off the raid windows loads fine and the disks check out ok.

Does anyone have any idea what went wrong and more importantly how to fix it? (Preferably without having to do the alternate install from scratch)
Thanks for your help.

---

