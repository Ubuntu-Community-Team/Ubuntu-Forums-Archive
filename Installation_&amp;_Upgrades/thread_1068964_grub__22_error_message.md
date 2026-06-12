---
title: "grub  22 error message"
date: 2009-02-13
forum: Installation &amp; Upgrades
---

### Post by je112 on 2009-02-13
Hi,

After deleting Ubuntu linux from a partition in " Partition Magic" in attempt to uninstall it, windows will not start. Information from Symantec knowlege base was something that "grub should have been installed to a partitiion instead of MBR"?? The instructions from previous ubuntu threads to restore Windows did not work as once in windows recovery console from the cd, the administrator password "Administrator" was not accepted as valid, so no further progess could be made. The computer will no longer boot from the downloaded version of ubuntu, but it will boot from a second ubuntu disc from a book. I also downloaded Super Grub Disk on to a disk which it runs, but am not sure what to do, I am complete newbie. I would appreciate advise on how I could fix this, I would like to get windows back and have it boot up first, then ubuntu.

---

### Post by jpaulb on 2009-02-13
Use a DOS disk and type
fdisk /mbr (not sure which way the'/\' goes
this should reconstruct the MBR

---

### Post by je112 on 2009-02-15
Thanks for reply, but I do not have a DOS disk or a floppy drive, just the windows xp disc, and an ubuntu live cd from a book. In the boot section of the ubuntu live cd, I typed fdisk/mbr and pressed enter, the response was "could not find kernel image: fdisk/mbr".


Je112

---

### Post by Pumalite on 2009-02-15
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

---

### Post by je112 on 2009-02-15
Thanks for the link, but I have previously glanced over that page and carried out solutions such as  the "fddisk\mbr" command which did not work as mentioned [B]windows will not accept the "password". However it is now fixed. After entering some commands in Super Grub Disk, grub is replaced and the pc boots up.


je112

---

