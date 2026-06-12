---
title: "2nd hard-drive format question"
date: 2009-01-17
forum: Hardware
---

### Post by shrekfx on 2009-01-17
I just reformated and installed only ubuntu on my primiary harddrive. I plan on making a small partition for windows later, and another for other linux distros.. Well my question is for my back up drive, what should the filesystem be for it so i can access files on both windows and linux..

---

### Post by taurus on 2009-01-17
You can use either ntfs or ext3 since Ubuntu can read and write to ntfs filesystem with ntfs-3g while windows can now access ext2/3 with fs-driver, [http://www.fs-driver.org/](http://www.fs-driver.org/).

---

### Post by shrekfx on 2009-01-17
what would you recomend?

---

### Post by taurus on 2009-01-17
Personally, I would go with ext3 (no fat32/vfat or ntfs crap) but it's probably easier for you to go with ntfs if you plan to have windows on that machine later.

---

### Post by shrekfx on 2009-01-17
ya. only thing i really would use windows for is to sync my g/f Moto Q, some blackberry stuff, and some apps that i cant use in Linux.

---

