---
title: "Removed CD-Rom but still &quot;recognised&quot;"
date: 2005-09-25
forum: Hardware &amp; Laptops
---

### Post by redmoon on 2005-09-25
Hello,

I removed a CD rom from my PC but Ubuntu still seems to recognise it and list it under "Computer" as "CD-ROM 1". How do I stop this and perform any other necessary steps since the hardare is no longer installed.

Cheers.

---

### Post by Tiede on 2005-09-25
It must still be lingering somewhere in /etc/fstab
open fstab with ```
sudo gedit /etc/fstab
``` and comment out the cdrom line.

---

