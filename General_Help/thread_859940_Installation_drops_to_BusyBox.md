---
title: "Installation drops to BusyBox"
date: 2008-07-15
forum: General Help
---

### Post by Brian88 on 2008-07-15
I have Ubuntu 8.04 (ShipIt CD) installed via Wubi from Windows XP SP2. I give the Ubuntu 10 GB space. I never booted XP after installing Ubuntu. Three days ago I booted XP, and then I booted back to Ubuntu. But Ubuntu doesn't fire up GNOME, but drop me to the BusyBox. How to fix it because I still need the data in /home folder of the ubuntu installations.

---

### Post by ago on 2008-07-15
Probably you did not shutdown properly. Boot into windows, run chkdsk /r on the drive where you installed wubi, reboot cleanly, and try again.

---

### Post by plastichero on 2008-07-15
Do you stuck at some point with this prompt?

[COLOR="DarkOrange"]Busybox v1.1.3 (Debian 1.1.1.3-5ubunu7) Bult-in shell (ash)
Enter help for a list of built in commands.
(initramfs)[/COLOR]

I also got the same thing and was astonished. The solution is simple: From windows, after running the WUBI installer, replce "quiet splash" with "all_generic_ide" in the file g:\ubuntu\disks\boot\grub\menu.lst and reboot. Hope it works. (Here G: was the drive that is selected for Ubuntu installation, it may be different for you)

also, is your drive FAT32 formatted? make it NTFS.

---

### Post by Brian88 on 2008-07-18
> **plastichero said:**
> Do you stuck at some point with this prompt?

[COLOR="DarkOrange"]Busybox v1.1.3 (Debian 1.1.1.3-5ubunu7) Bult-in shell (ash)
Enter help for a list of built in commands.
(initramfs)[/COLOR]

I also got the same thing and was astonished. The solution is simple: From windows, after running the WUBI installer, replce "quiet splash" with "all_generic_ide" in the file g:\ubuntu\disks\boot\grub\menu.lst and reboot. Hope it works. (Here G: was the drive that is selected for Ubuntu installation, it may be different for you)

also, is your drive FAT32 formatted? make it NTFS.
At install my disk was NTFS. I install it on D:\

I will try. Now I'm on Windows. I will reply if I get on ubuntu and can boot properly. Thanks!

---

