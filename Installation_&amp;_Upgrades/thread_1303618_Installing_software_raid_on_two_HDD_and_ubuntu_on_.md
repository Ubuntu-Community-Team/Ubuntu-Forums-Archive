---
title: "Installing software raid on two HDD and ubuntu on one SSD?"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by willis575 on 2009-10-28
Good afternoon!

I would like to install software raid0 on two hard drives and the OS on a solid state drive. I am using the karmic alternate installer and have gotten to the create MD device screen, but it is only giving me an option to create use the ssd for raid. Any help would be appreciated!

---

### Post by peterx2 on 2009-10-28
I too am in the same boat. ( 64b with 2 SATA 120g drives.. However....
I used desktop cd and when it came to the partitioner, it only offered RAID with the combined space of the two drives (240gb) (essentially defaulted to RAID0) it offered to make it auto partition in the combine space using all space available, so I accepted that and ran a perfect install until it came to Grub2 which failed. but offered to reboot.  since grub1 cant find grub2 files and they arent that compatible and I couldnt boot the system (grub error 2). I gave up on that run..The Alt disk comes up with a blank partition screen, meaning it wouldnt work with whatever is in the mbr.
Look carefully using the live disk at disk utility menu item. It does give you a clue. if it is confused, find some way to make sure that all space is unallocated before starting install.. (gparted doesnt penetrate RAID space) and grub1 tools are kind of useless because of the change in architecture of grub1 to 2. If you are successful I hope you post it here.. good luck

---

### Post by willis575 on 2009-10-28
I've been searching and trying all day... I was hoping to get a normal install done to the ssd and see if I could try to create raid on the two other drives post install, but the xorg seems to crash in karmic on machines with nvidia cards. I will keep trying and will post any success here.

---

### Post by willis575 on 2009-11-12
bump

---

