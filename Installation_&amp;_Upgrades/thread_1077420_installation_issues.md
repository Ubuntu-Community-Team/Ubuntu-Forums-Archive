---
title: "installation issues"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by coldsteel2001 on 2009-02-22
My hdd setup is as follows:
/dev/sda1 (hd0) 8Gb /
/dev/sdb1 (hd1) 20Gb /home
spare hdd not plugged in 6Gb

I had issues after installation where my system couldn't boot ubuntu from my primary partition. It comes up with a windows bootloader error stating that the system disk can't be found...which has nothing to do with grub.
I've checked the grub files (menu.lst, the drive map file) and everything checks out...yet the system won't even touch grub unless I boot the system with my Windows 2000 cd in the drive.
I've tried reformatting sda1 and making sure grub was installed properly, but the system still won't boot off that hdd. I have m spare 6Gb drive I could use but if I do then I have one question...can I still keep my user folder (/home/h3x) on sdb1 if I mount the drive as /home in installation? That is my only worry...as I have tried using the partition manager (GParted) in ubuntu (and the ubuntu live cd) to check all the options for the partition (flags etc).

Any advice or help offered would be greatly appreciated to ease my month long pain, thanks.

---

### Post by coldsteel2001 on 2009-02-22
This is going to sound really stupid but resetting the bios did nothing, yet after removing the mains power cable and loading optimum defaults, the system now boots grub and ubuntu...yay!
I feel so retarded after that lol, well at least now my windows 2000 cd can finally go back in my cd stack.

Thanks anyways.

---

