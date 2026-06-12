---
title: "Ipod Mounts as read only"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by earobinson on 2005-05-20
how can i stop my ipod from auto mounting as read only, i checked ect/fstab and there is no entry there i just plug in the ipod and it used to work and it no longer does?

thanks

---

### Post by lildude on 2005-05-20
[QUOTE=earobinson]how can i stop my ipod from auto mounting as read only, i checked ect/fstab and there is no entry there i just plug in the ipod and it used to work and it no longer does?

thanks[/QUOTE]
 Check the perms of the underlying device  This could be udev giving the underlying device read-only permissions, or it could be the gnome-volume-manager mounting the device read only.

Once we know the perms of the underlying device, we can work out where things are going wrong.

If the underlying device is set with read only permissions, check the corresponding entry in the /etc/udev/permissions.d/* files or the /etc/udev/permissions.rules file.

HTH

---

