---
title: "Unmounting usb disks in XFCE"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by jellyfisharepretty on 2006-04-13
Hi all, first post here in the ubuntu forums :) 

Anyway, I searched the forums for a way to automount usb disks in xfce, what I found is that if gnome-volume-manager is started along with XFCE, the usb disks will automount.

This works beautifully, and icon for the flash drive even appears on my desktop, just like in gnome.  However, upon right-clicking on the icon there is no option for unmounting the drive (there is such and option in gnome).

Anyone know of a way to cleanly unmount these drives in XFCE in combination with gnome-volume-manager ?

Thanks!

EDIT: Forgot to mention, using ubuntu breezy

---

### Post by aysiu on 2006-04-13
I've never had that problem in XFCE. If I use *gnome-volume-manager*, there's always an **unmount volume** option in the right-click context menu.

You can always unmount it from the command-line, though. ```
df -h
``` to find where it is. If it's /dev/sda1 do ```
sudo umount /dev/sda1
```

---

### Post by jellyfisharepretty on 2006-04-15
Err, you're right !  I could have sworn the other there wasn't this option.

No matter, mystery solved.  Thank you!

---

