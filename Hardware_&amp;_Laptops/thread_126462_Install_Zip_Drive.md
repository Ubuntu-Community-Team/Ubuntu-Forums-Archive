---
title: "Install Zip Drive"
date: 2006-02-06
forum: Hardware &amp; Laptops
---

### Post by souteneur3190 on 2006-02-06
I just installed a 250mb Iomega Zip Drive on my Ubuntu Breezy Computer.  Ubuntu seems to detect it but when i try to mount i get the follwing message...

Unable to mount the selected volums
Details:
Error: Could not execute Pmount

---

### Post by 3rdalbum on 2006-02-06
How is the drive connected? IDE, SCSI, USB or Firewire?

---

### Post by vaultdweller on 2006-02-07
im having the same trouble, my zip drive is connected through ide

---

### Post by souteneur3190 on 2006-02-07
mine too is IDE

---

### Post by ancient_ee on 2006-02-22
Ditto for my IDE 250 zip drive. Tried both master and slave. The boot log says "hdd: The disk reports a capacity of 250640384 bytes, but the drive only handles 250609664" (hdd is my zip drive). This bootup error message (I also get an on-screen (red text) boot error for [COLOR="Red"]loading local file systems[/COLOR], which I believe concerns the zip drive. These errors persisted after reformatting the zip media using WinXP.

---

### Post by ancient_ee on 2006-02-22
UPDATE: Fixed all the errror messages and the drive mounts now! I just followed the directions for "HOWTO: Get your Iomega Zip Drive to work" at [http://ubuntuforums.org/archive/index.php/t-12074.html](http://ubuntuforums.org/archive/index.php/t-12074.html) (works for my Ubuntu 5.10).

---

