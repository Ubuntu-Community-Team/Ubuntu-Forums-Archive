---
title: "Dualbooting -- windows will not boot from GRUB"
date: 2008-07-21
forum: Hardware
---

### Post by crayzeigh on 2008-07-21
Situation is exactly as it sounds.

Let me lay out the hard drive situation:

I have 4 Hard disks. Two sata drives: disc one has GRUB and Ubuntu, they're listed as /dev/sda (the startub disc) and /dev/sdb (Old NTFS storage partition I haven't finished cleaning up yet). All good so far. Then I have two IDE drives. IDE1 is the master with a clean install of WinXP Professional (long story about why I need to dual boot) and IDE2 is completely unallocated. The issue here: in ubuntu IDE1 is /dev/sdc and IDE2 is /dev/sdd. Still, shouldn't be too much of a problem.

GRUB lists the drives as hd0 - hd3 in the order of sda, sdb, sdc, sdd making the IDE drives hd2 and hd3 respectively as master and slave.

So I try the norma procedure from booting from a second hard disk with winXP

```

map (hd0) (hd2)
map (hd2) (hd0)
rootnoverify (hd2,0)
makeactive
chainloader +1
boot
```

Normal deal, screen refreshes, lights up as a black screen no text and.... no windows logo.

I have even tried to just boot from the drive directly without mapping and it doesn't even get that far.

The only way I can get it to boot so far is to switch HDD0 to the primary boot drive in the BIOS instead of "SCSI/SATA."

Searching around and after playing with the menu.lst a bit, I decide it would be a good idea to have a backup boot disk and download superGRUB disc. And I figure, why not, lets see if there's some process superGRUB has that will boot this damn winXP.

Pop in the disc, restart: SUPERGRUB! I try the "boot winXP from a second hard disk" and I notice that my drives are listed differently! hd0 (according to SuperGRUB) is now IDE1 or HDD0 in BIOS. So, of course, using the simple windows boot command SuperGRUB boots winXP with no problem. 

Of course, popping in superGRUB every time I want to use windows is a complete hassle because I need it to be easy enough that anyone in my house can start up the computer, and just select "Windows XP" from the list and bounce up without an issue.

Moral of the story: "HELP!"

Is there a way I can get GRUB (on sda) to think of the drives as hda, hdb, sda, sdb and rank them as hd0-3 respectively? Or do I have to install grub on my MBR of IDE1 in order for it to work (another less than ideal situation, but if it's what I got, it's what I got)?

P.S. If someone has already posted a solution I apologise, but I've been working on this issue for two days checking forums all over the place and have not been able to fix anything yet.

P.P.S. I also apologise if this is absolutely the wrong place to post this, it seemed the most relevant.

---

### Post by logos34 on 2008-07-21
Have you tried (hd1,0), with and without the map lines? 

Mixed sata-ide system almost throw grub for a loop (grub seems to be hardcoded to scan the ide channels first)

---

### Post by crayzeigh on 2008-07-22
It's (hd2,0) but yes.

```

rootnoverify (hd2,0)
makeactive
chainloader +1
boot

```

System hangs at "Starting up..." but at least from here I can give it the 3-finger-salute to reboot.

---

### Post by crayzeigh on 2008-07-22
Not what I wanted to do, but I got it working the dirty way.

I put grub on the MBR and booted it that way. That way I boot from HDD0 (sdc) which makes GRUB call that drive (hd0) windows boots fine.

Ran superGRUB>GRUB ===> MBR & !LINUX! (>=2) Manual
chose the Ubuntu partition to pull Grub from, chose the Ubuntu partition to boot from, got the Grub menu and fixed the HD references and booted fine.

Booted into Ubuntu, edited the hd references in menu.lst (changed all occurances of (hd0) to (hd2) and vice versa) rebooted, menu options work flawlessly.


If anyone comes up with a better solution to boot Grub without having to put it in the same boot record as ntldr, Please let me know, But since GRUB is still on my ubuntu partition, all I have to do is restore /boot/grub/menu.lst from my backup and I suppose no harm done if I ever remove that drive.

---

### Post by logos34 on 2008-07-22
> **crayzeigh said:**
> Not what I wanted to do, but I got it working the dirty way.

I put grub on the MBR and booted it that way. That way I boot from HDD0 (sdc) which makes GRUB call that drive (hd0) windows boots fine.

Ran superGRUB>GRUB ===> MBR & !LINUX! (>=2) Manual
chose the Ubuntu partition to pull Grub from, chose the Ubuntu partition to boot from, got the Grub menu and fixed the HD references and booted fine.

Booted into Ubuntu, edited the hd references in menu.lst (changed all occurances of (hd0) to (hd2) and vice versa) rebooted, menu options work flawlessly.

If anyone comes up with a better solution to boot Grub without having to put it in the same boot record as ntldr, Please let me know, But since GRUB is still on my ubuntu partition, all I have to do is restore /boot/grub/menu.lst from my backup and I suppose no harm done if I ever remove that drive.

That probably would have been my next suggestion...Either that or make a Grub boot floppy or cd.

As to your concluding comments, you could chainload linux from windows bootloader, which at least would avoid any disruption caused by removing the linux drive at a later date.  See my post in this thread:
[http://ubuntuforums.org/showpost.php?p=5432439&postcount=3](http://ubuntuforums.org/showpost.php?p=5432439&postcount=3)

---

