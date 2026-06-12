---
title: "black screen with fresh install"
date: 2009-05-13
forum: Hardware
---

### Post by Voodo on 2009-05-13
Hi, i've just installed Xubuntu 9.04 on my old laptop (Fujitsu Siemens Amilo D, 1ghz processor, 128 mbyte ram, 10 giga HDD) and i have a problem.

After the GRUB loader finishes i get a completely black screen, no cursor, no anything.
a part of the screen flashes with a green/red-ish color than it goes completely black, only thing i can do is shut down the computer, nothing else.

already tried the recovery mode with repairing packages and trying to fix graphics problem, didnt help

any guess?

Voodo

---

### Post by Jasper84 on 2009-05-30
Same problem here, on a Fujitsu Siemens Amilo LA1703. (Incidentally, i got a horizontal line that blinked once before getting a blank screen.) I was running only from the CD.

Trying it with 'safe graphics mode' (F4 at the menu when booting from CD), it works. 

I think i will try adding xforcevesa [http://www.amilo-forum.com/topic,1557,-La1703-Boot-problem-Ubuntu-Fedora-OpenSuse.html](http://www.amilo-forum.com/topic,1557,-La1703-Boot-problem-Ubuntu-Fedora-OpenSuse.html) to the installation and hope it works.

Edit: weird, i didn't have to change anything for it to work. It won't go to fancier visual effects though. Think i'll have to change /etc/X11/xorg.conf

---

### Post by UrbenLegend on 2009-05-30
Maybe Xorg is trying to switch to a resolution that your display cannot go to? Could explain the flash.

---

### Post by gillbert on 2010-08-28
this worked for me:

[http://ubuntuforums.org/showthread.php?t=1560710&highlight=Amilo+LA1703](http://ubuntuforums.org/showthread.php?t=1560710&highlight=Amilo+LA1703)

---

