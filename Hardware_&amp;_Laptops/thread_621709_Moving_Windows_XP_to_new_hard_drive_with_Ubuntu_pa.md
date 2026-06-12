---
title: "Moving Windows XP to new hard drive with Ubuntu partition"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by dhinge on 2007-11-24
I have Windows XP on a 20GB laptop, and want to move it to a 120GB drive with Ubuntu 6 on it (56GB partition). Has anyone done this, and what was successful?

---

### Post by eggdeng on 2007-11-24
Copying the XP partition would be more trouble than it's worth & with no guarantee of success. If you really want to go that way, you could look into ghost (proprietary) gparted or partimage. Better to do a fresh install, just make sure to install XP before ubuntu.

---

### Post by dhinge on 2007-11-24
The Windows XP came proprietary on a used laptop I bought. I copied over XP using a DiscWizard (Seagate) image... GRUB notices the XP install, but gives Error 22 when I select to boot it. Are there any recommendable boot software that I can boot from a floppy to clear up this booting stuff? I can handle the WinXP files and GRUB config, but I've yet to find any good boot configuration software that will straighten out actual MBR issues.... arrg

---

### Post by dhinge on 2007-11-25
Alright, I bit the bullet and copied the image of Windows XP to the hard drive directly, erasing Ubuntu. I then installed Ubuntu, and everything works peachy keen.

---

