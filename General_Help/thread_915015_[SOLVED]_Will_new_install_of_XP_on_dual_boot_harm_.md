---
title: "[SOLVED] Will new install of XP on dual boot harm Ubuntu"
date: 2008-09-09
forum: General Help
---

### Post by nyborjare on 2008-09-09
Folks
I might have to perform a new install of my XP on my dual boot system.
Will this damage the Ubuntu installation :confused:

Appreciate any support in this matter.

regards
Michael

---

### Post by Sycron on 2008-09-09
No but you have to reinstall GRUB. Have a look over here [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) . Hope it helps and good luck.

---

### Post by tuxxy on 2008-09-09
Not if you install it correctly to the same partition, you may need to re-install GRUB

---

### Post by Rocket2DMn on 2008-09-09
Installing Windows will overwrite the MBR, but this can be worked around by re-installing GRUB to the MBR.  Have a look at [uhelp]community/RecoveringUbuntuAfterInstallingWindows[/uhelp] for a variety of directions on doing this.  It's not actually as complicated as it may first appear.  The Super Grub Disk can do it for you automatically if you want - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

> **Sycron said:**
> Yes

Very helpful.

---

### Post by Sycron on 2008-09-09
> **Rocket2DMn said:**
> Very helpful.

Sorry, but I was late and that was all I could say.

---

### Post by nyborjare on 2008-09-10
Thank&#347; folks for your support in this.
Will study and go.....:)

michael

Used the Super Grub CD and all is back to normal again / Michael

---

