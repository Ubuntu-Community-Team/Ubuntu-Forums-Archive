---
title: "Grub loading stage 1.5"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by PEC321 on 2009-05-24
[SIZE=2]I had installed on my Toshiba laptop Vista/Ubuntu 9.04 and decided to re-install XP, the install, it finishes OK, but instead of XP I get a black screen with:
[B] GRUB LOADING STAGE 1.5
GRUB LOADING PLEASE WAIT
ERROR22. [/B]
I have tried EVERYTHING to wipe the HD, several re-installs of XP, tries of Ubuntu and delete & format HD with Partition Magic without results the GRUB message always blocks running the OS. Help please, I am far from being computer illiterate, but not very good with commands.[/SIZE]

---

### Post by mikezila on 2009-05-24
Grub is probably in the mbr.

You can fix that by either using a windows setup disk's recovery console to do a "fixmbr" or "fdisk /mbr".

You can also fix it by using a Ubuntu livecd and using the partition manager to set a disk label.  Set it to MSDOS.  Start up the install disk, and up at the top hit "System"->"Admin"->"Partition Editor".  Then in that pick at the top "Device" and pick the only option (should be "Create Partition Table" or similar).  Open up the advanced and pick MSDOS.

That nukes everything that is nukeable on the harddisk, so that'll fix whatever is ailing you.

---

### Post by PEC321 on 2009-05-25
Thanks guys, problem solved it was a defective download CD of Ubuntu, got the mailed CD today and it woks perfecty, so far I am impressed

---

