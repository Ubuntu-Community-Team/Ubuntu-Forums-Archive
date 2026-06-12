---
title: "Not recognizing dvd/cd-rom drive"
date: 2006-10-07
forum: Hardware &amp; Laptops
---

### Post by lordgiovanni on 2006-10-07
After I installed ubuntu, I tried booting up windows.  It made me run chkdisk and after that ran it restart.  When I finally got back into windows my dvd/cd-rom drive would not show up.  It doesnt seem to appear in both ubuntu or windows.  In ubuntu it says cd-rom 1, but when i try to open it, i receive the error: mount: special device /dev/scd0 does not exist.

Ususally during my system start up, it will check the ram then say something about my mouse and keyboard and cd-rom drive before windows would boot.  It seems to be skipping that last part and going straight to the boot loader.
What do I need to do?

I have a Hypersonic CX7.

---

### Post by xyz on 2006-10-07
Hi-
Have you tried to run this command in a console:
```
sudo mount /media/cdrom0/ -o unhide

```

---

### Post by Kateikyoushi on 2006-10-07
He wrote it doesn't show up in windows either.
Can you see the drive in the BIOS ?

---

### Post by lordgiovanni on 2006-10-07
> **xyz said:**
> Hi-
Have you tried to run this command in a console:
```
sudo mount /media/cdrom0/ -o unhide

```

yea, i receive the same message: mount: special device /dev/scd0 does not exist


I just checked and it is appearing in my BIOS.  I'm not really sure what could be wrong with it.  If I run Ubuntu with the live CD, it correctly labels my cd-rw/dvd drive and allows me to explore through the cd.  I don't know if that means anything or not.

---

