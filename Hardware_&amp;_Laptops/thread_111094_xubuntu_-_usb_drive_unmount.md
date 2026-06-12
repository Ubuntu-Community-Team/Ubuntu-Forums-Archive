---
title: "xubuntu - usb drive unmount"
date: 2006-01-01
forum: Hardware &amp; Laptops
---

### Post by Chrissie on 2006-01-01
To read my usb drive in xubuntu, I've done
> gnome-volume-manager&
Now xubuntu happily recognizes my usb drive when I slip it in.

But what do I have to do to remove it? Can I just snap it out? In xubuntu there are no icons on the desktop, so the only place where I see it is in rox (the file manager).
If I right-click on it in rox, I get the following:
> Unmounting /media/USB DISK
umount: /media/USB DISK is not in the fstab (and you are not root)
Unmount failed
Done
There was one error.

I had a look at fstab mount manager... it's scaring me.

Any help welcome, thanks
Christel

---

### Post by kaamos on 2006-01-01
I see no problem with just snapping it out.. Just make sure the drive is no longer writing data (no leds blinking etc). If you want to make sure, you can unmount it in terminal with "eject sda1". If you have more usb-drives it could be sda2 and so on..

---

### Post by Chrissie on 2006-01-01
Thank you thank you!
It's great to be able to just snap it out.
C-

---

