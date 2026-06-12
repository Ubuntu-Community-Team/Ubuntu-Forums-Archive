---
title: "[SOLVED] cant see external hdd"
date: 2008-11-08
forum: General Help
---

### Post by thestig_992 on 2008-11-08
I have an external hdd that i borrowed from a friend for tempoarily abcking some stuff up, which i have used before (exact same drive). This time, however, I cant see the drive at all. It is a usb drive, definietly on, and the ubuntu places menu cant see it, nor can lsusb command. Any suggestions?

---

### Post by Afkpuz on 2008-11-09
Install gparted and see if that can detect it.  I've had a problem that certain usb plugs, especially ones on the front of the tower would not work correctly when I plugged in a usb hard drive.  If gparted doesn't see it, try using a different usb plug.  If it does see it, then you just need to set up your fstab.

---

### Post by thestig_992 on 2008-11-09
Swapping ports doesnt help, I'll try in a few minutes on windows, just incase. Also, isnt fstab the file that tells the OS what needs to be mounted at boot? If Im wrong, what sort of thing should i put into fstab?

---

### Post by thestig_992 on 2008-11-09
solved, turns out my cable was broken; sorry for the trouble...

---

