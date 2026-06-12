---
title: "Mount options not in fstab"
date: 2008-05-19
forum: Hardware
---

### Post by noynac on 2008-05-19
Is there any way to alter the options that linux uses to mount external drives that are not mounted through fstab. I want to change the uid and gid of external ntfs and vfat usb drives WITHOUT putting them in fstab. Thanks!

---

### Post by sdennie on 2008-05-19
Yes, you can create udev rules.  It's more complicated than fstab but, you can find a guide here: [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html).  The udev rules in Ubuntu are found in /etc/udev/rules.d.

---

### Post by noynac on 2008-05-19
Thanks for the response and helpful link. That's just what I was looking for.

---

