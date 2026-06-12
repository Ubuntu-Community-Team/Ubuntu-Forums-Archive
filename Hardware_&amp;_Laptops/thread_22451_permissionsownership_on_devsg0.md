---
title: "permissions/ownership on /dev/sg0"
date: 2005-03-27
forum: Hardware &amp; Laptops
---

### Post by fredex on 2005-03-27
Just set up a Ubuntu box to host my scsi scanner. Every time I boot the machine I have to go change the owner (or permissions) on /dev/sg0. How can I make it so they persist?

Thanks!

---

### Post by alastair on 2005-03-28
This is "udev" probably. Look at :

/etc/udev/permissions.d/udev.permissions

---

### Post by fredex on 2005-03-30
Thanks, I'll check that out when I get home.

---

