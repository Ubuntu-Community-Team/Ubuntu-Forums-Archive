---
title: "Formatted Hardrive, Grub Error 22"
date: 2008-12-30
forum: Installation &amp; Upgrades
---

### Post by Sashin on 2008-12-30
I used to dual boot Ubuntu Hardy and Kubuntu Intrepid. On two seperate internal hardrives

I wasn't using Kubuntu so I decided to install Linux Mint on that hard drive. However I didn't like it so I formatted that hardrive.

Now when I boot I get the Grub error 22. I can't even boot from CD, but I can from USB. Is there anyway to fix this?

---

### Post by Sashin on 2008-12-30
Please, is there anyone that can help?

---

### Post by Pumalite on 2008-12-30
Have you tried to change the boot order of your hard drives in BIOS?
If no results; read this:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by Sashin on 2008-12-30
Right now it boots the CD first, then my main hardrive(ubuntu) then my blank one.

---

### Post by Pumalite on 2008-12-30
Try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Sashin on 2008-12-30
Don't worry I've found a temporary fix. By reinstalling Mint, using it's grub and modifying it's grub menu.

Is there a reason that the bootloader by default is on a different hard disk?

---

### Post by Pumalite on 2008-12-30
Grub by default is installed in your first hard drive.

---

