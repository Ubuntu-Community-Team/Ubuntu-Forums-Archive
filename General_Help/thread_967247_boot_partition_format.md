---
title: "/boot partition format"
date: 2008-11-01
forum: General Help
---

### Post by xinix on 2008-11-01
Is it possible to have a /boot partition in a format that can be read and written by Linux and Windows?
Sadly I have to boot into XP just to watch Netflix watch-it-now stuff.  But this computer runs without a keyboard (mythtv box). So switching OS's is a hassle that requires me to get a keyboard from my office and plug it in just to select a different OS in grub.
I had an idea that would avoid this hassle for me.  It is to have a shutdown script that switches the default OS in /boot/grub/menu.lst for me.  Then when I want to switch to Windows I could run the "Shutdown and switch to XP" script, and then boot back to Linux from Windows with a similar script.  So, what are my format options, NTFS, MSDOS?

Thanks

---

### Post by dcstar on 2008-11-01
> **xinix said:**
> Is it possible to have a /boot partition in a format that can be read and written by Linux and Windows?
Sadly I have to boot into XP just to watch Netflix watch-it-now stuff.  But this computer runs without a keyboard (mythtv box). So switching OS's is a hassle that requires me to get a keyboard from my office and plug it in just to select a different OS in grub.
I had an idea that would avoid this hassle for me.  It is to have a shutdown script that switches the default OS in /boot/grub/menu.lst for me.  Then when I want to switch to Windows I could run the "Shutdown and switch to XP" script, and then boot back to Linux from Windows with a similar script.  So, what are my format options, NTFS, MSDOS?

Thanks

Just have various copies of menu.lst with the default OS number set differently, and have a script copy them to be menu.lst before rebooting.

---

### Post by xinix on 2008-11-02
That is exactly what I was thinking, but what I'm not sure about is if my /boot partition can be in a format that Windows can read and write to (eg, MSDOS or NTFS).  I know it's super easy to tell Linux to switch my menu.lst but if I can't get Windows to switch it back to the one that would boot Linux, then I'm still going to have to go get a keyboard; which would defeat the purpose of the script.

---

