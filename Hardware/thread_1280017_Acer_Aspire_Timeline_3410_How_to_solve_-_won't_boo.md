---
title: "Acer Aspire Timeline 3410 How to solve - won't boot after install"
date: 2009-10-01
forum: Hardware
---

### Post by wilsonandyb on 2009-10-01
This may be an obvious newbie error, and also maybe posted in the wrong place, but here goes...

Acer Aspire Timeline 3410 - after installing Ubuntu 9.04 you may need to go into the bios and change Sata mode to IDE, or you'll find that it won't boot from the hard drive, even though it will boot from the live cd and work fine.

For noobs like me, here is how:

press F2 to enter bios
choose MAIN from the menu along the top
choose SATA mode
use F5/F5 to switch from AHCI to IDE 
press F10 to save and exit.

Should boot up fine.

Full credit to this post hwhere I found the solution:
[http://forum.notebookreview.com/showthread.php?p=5057077#post5057077](http://forum.notebookreview.com/showthread.php?p=5057077#post5057077)

---

### Post by PatrickVogeli on 2009-10-01
already posted in this forum.. Better solution is to disable ncq adding the grub parameter libata.force=noncq and enabling ahci in bios again.

---

