---
title: "CD drawer locks after inserting disk and some problems with memory cards..."
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by Dr-ROX on 2005-06-27
*Problems:*

After inserting a CD, system locks the drawer - no reaction even after clicking the open button on the device. I´m using Gnome panel applet for drive unmounting - then the drawer opens itself.
-
Is it possible to make CD opening more traditionall, when button push on the physical device opens the CD drawer?

-----

*Problems:*

I have TRENDnet all-in-one memory card reader. It works good, but there are also some problems with unmounting. When I plug in the device and some cards, system recognizes them and mounts automatically. Device icons apears on the desktop. But after taking one card out, it remains mounted and icon remains on desktop until I plug the whole reader off. On SuSE all worked fine - cards disapeared from desktop after taking them out without pluging the reader off.
-
Is it possible to solve this?

Thanks.

---

### Post by Navin_Johnson on 2005-06-27
For the CD Drive:
This is perhaps more of a work around or alternative solution rather than the answer you're looking for but here it is anyhow:

The CD gets locked while it is mounted (which Ubuntu automagically does).  In order to eject it you either need to manually unmount it (as you've already done) or else you can right click on the icon of the CD and select eject.

There may be a way to make the drive act like a wintel cdrom where you simply push the physical eject button, but I'm sorry I don't know what it is.  Perhaps someone else will post a better answer.

Best,
Navin Johnson (eric)

---

### Post by htinn on 2005-12-25
I think a software eject triggered by the physical button would be a great idea, but one thing you can do to simplify is to create a custom launcher on your panel with an eject icon in it which simply performs this command:

eject -r

---

### Post by ubuntuuser on 2005-12-28
This was really annoying me, so I did a search on the forum and found```

sudo sh -c 'echo "dev.cdrom.lock=0" >> /etc/sysctl.conf'
```
This helps.

---

