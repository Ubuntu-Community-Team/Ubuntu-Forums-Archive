---
title: "Plugging in external hard drive freezes desktop"
date: 2011-01-03
forum: Hardware
---

### Post by ladysorka on 2011-01-03
I was given a Western Digital My Passport, USB 3.0 500 GB for the holiday.  I do not have a 3.0 card, but it is supposed to be backwards compatible.  However, when I attempt to plug the drive in, immediately upon plugging the USB cord into my laptop the desktop completely freezes and I end up having to do a hard reboot.

I tried connecting the drive before the turning the computer on, which gave me access to both the drive and the desktop, however I could not remove the drive (clicking "safely remove drive" caused the icon to disappear for about 3 seconds and then reappear and the drive's folder would pop up).  Gparted told me it couldn't find the drive's mount point and wouldn't unmount the drive either, meaning I also can't reformat it.

Anybody have any idea what's up?   I have a number of other WD externals and have never had an issue with them - though, granted, this is my first 3.0.  I'm running Ubuntu 10.10 on a zareason Verix laptop.

---

### Post by Fafler on 2011-01-04
Try pressing ctrl + alt + F1. This should give you a text based login screen. Now connect the drive and hopefully it will dump some useful text before crashing.

Also reboot with the drive connected and do a
```
dmesg | grep sd
```

---

