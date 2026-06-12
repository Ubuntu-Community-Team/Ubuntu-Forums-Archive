---
title: "Removing Ubuntu from my Laptop"
date: 2008-02-06
forum: Hardware &amp; Laptops
---

### Post by core2boomer on 2008-02-06
ok, i decided i only want to use Ubuntu on my desktop and want to remove it from my laptop.

i have a HP dv9500 laptop with dual hard drives. i currently have Ubuntu installed on the a 20gig partition on the DATA drive (not on my Vista OS drive). 

the other day i tried deleting the 20gig partition to erase Ubuntu on my DATA drive drive.

**the problem:** when i rebooted after ubuntu was deleted, the GRUB loading screen still came up after the bios screen, and it wont load Windows because i deleted the Ubuntu partition. it just says loading GRUB then i get some error message. there was no way i could get windows to load! :( so i ended up reinstalling Ubuntu with the live CD for the mean time until i figure out how to correctly remove Ubuntu.

so how can i remove the GRUB loading screen after the Ubuntu partition is deleted?

thanks 
Jim

---

### Post by pmshirey on 2008-02-06
This may be what you need to do, take all your windows files and settings (Found under my computer, and drive C: ),burn them onto a DVD if you can, or a bunch of CDs, then re look for a system restore disk for your computer, and pop that in and boot it. If that doesn't work, re install windows, then after windows is installed, pop the CDs or DVD into your computer and load the files and settings on (probably with files and setting transfer.)

---

### Post by gruhland on 2008-02-06
You have to change the ID number of the windows partition I would assume. Grub will locate the partition by number but you have changed the IDs of the partitions by deleting one partition. When you start and Grub is coming up there is one F-button (F2 ?) to edit the start configuration. I cannot give you the number for the partition but maybe you can find it out or it's obviously.

---

### Post by osos on 2008-02-06
maybe this'll help [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by core2boomer on 2008-02-06
hey, thanks for the fast replies, i will try these when i get home tonight and let you know if they work.

---

### Post by eggdeng on 2008-02-06
The correct way to do this is by following [http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe]("http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe")
See post #18 by erfahren at [http://ubuntuforums.org/showthread.php?t=643213&page=2]("http://ubuntuforums.org/showthread.php?t=643213&page=2")

---

### Post by gruhland on 2008-02-07
Yes, MBRFix could be the right way to do. In your case you have to boot then from a CD to get it running, maybe with Windows PE or BartPE. Then you can copy MBRFix or maybe you can run it from CD or USB stick as well.

---

### Post by core2boomer on 2008-02-07
> **eggdeng said:**
> The correct way to do this is by following [http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe]("http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe")
See post #18 by erfahren at [http://ubuntuforums.org/showthread.php?t=643213&page=2]("http://ubuntuforums.org/showthread.php?t=643213&page=2")

WOO HOO, it worked :) thanks a lot!

---

