---
title: "USB Read Only Problem"
date: 2008-10-05
forum: General Help
---

### Post by arclightfire on 2008-10-05
Hi, I have been using a little USB drive for some time to backup my work.  Today upon using it I found the drive to now be read only.

I also use this USB on a windows machine at work.

I am using Ubuntu 8.04.1

Any suggestions?

---

### Post by shamusl on 2008-10-05
I am having the exact same problem. I plugged in my psp and it now shows that it's a read-only device. I need this fixed.

---

### Post by edyeeh on 2008-10-11
Try this forum.

[>>>USB DRIVE READ ONLY problem.]("http://ubuntuforums.org/showthread.php?t=899060&highlight=usb+drive+read+only")

---

### Post by Glace on 2010-11-03
For me to fix my read only usb drive:
[LIST]
[*]mount your usb drive
[*]open gparted (must be root)
[*]find you're drive in the menu (try different selections in the top right if you can't see it)
[*]right click -> unmount
[*]it loaded for a while then next time I mounted it it was like normal
[/LIST]

---

### Post by sikander3786 on 2010-11-03
Sometimes running a simple filesystem check helps sort the problem. You can run it from gparted or see the man page,

```
man fsck
```

---

### Post by ahalin on 2011-03-30
> **Glace said:**
> For me to fix my read only usb drive:
[LIST]
[*]mount your usb drive
[*]open gparted (must be root)
[*]find you're drive in the menu (try different selections in the top right if you can't see it)
[*]right click -> unmount
[*]it loaded for a while then next time I mounted it it was like normal
[/LIST]

The gparted trick worked a treat, thank you. It took a couple of goes before Ubuntu and Nautilus saw the USB thumb drive (as there is no mount option in gparted I just unplugged it a couple of times), but it did. :popcorn:

---

