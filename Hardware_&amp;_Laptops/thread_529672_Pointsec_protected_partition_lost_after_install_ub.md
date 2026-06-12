---
title: "Pointsec protected partition lost after install ubuntu"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by leovannys on 2007-08-19
used to have one Windos XP partition and it's protected by pointsec. I created a new partition with help of partition magic and installed Ubuntu in it. The usual way of modifying grub to add a (hd0,0) menu item doesn't work. it seems grub overwrite whatever pointsec has in MBR. I want to get back the 1st partition. Could any body help?

I did a lot of search over internet and somebody said I can boot with a windows XP disc and use the rescue console to run fixmbr and fixboot. First of all, I don't have a XP disc at the moment. Secondly, I want to make sure I am not making things any worse before I purchase an extra windows XP copy. 

Can anyone give me any advice for that? Greatly appreciated.

---

### Post by ba5e on 2007-10-14
Unfortunately, you will have to reinstall PointSec - GRUB has overwritten your MBR effectively disabling PointSec. Im not sure how you should go about this - maybe contact Pointsec.

Remember to back up the MBR & the encrypted drive in the future ;)

---

