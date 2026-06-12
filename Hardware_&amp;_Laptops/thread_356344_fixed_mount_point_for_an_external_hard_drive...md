---
title: "fixed mount point for an external hard drive.."
date: 2007-02-08
forum: Hardware &amp; Laptops
---

### Post by chikko on 2007-02-08
hey guys,

i'm now an owner of a new WD 500gb my book, and i'm trying to work something out here:

i already gparted it - two partitions (ex3, fat32) but now here's the problem..  every time i plug it in (USB for now - till i find a 6pin to 4pin connector for the firewire bus) my laptop, Edgy mounts it as two devices - "usbdisk" and "usbdisk-1"  (it sometimes gives it other names like "usbdisk-2" etc..)
i would really love to have a permanent mounting point for both partitions.
i tried reading some posts about mtab and fstab - i don't even know the difference between them..  tried everything i could - and all i could figure out is how to mount manually, using the mount command at the terminal..
any chance someone can explain the way to make both partitions mounted to a certain /media/folder every time i plug it in..?

thanks!

---

### Post by chikko on 2007-02-09
poping it up again.. ](*,) 

anyone..? :(

---

### Post by robenroute on 2007-02-09
See [here]("http://ubuntuforums.org/showthread.php?t=344839"). I hope that helps.

---

### Post by raublekick on 2007-02-09
hmm i have been looking for the same thing, i always wondered why ext2/3 partitions didn't get labels by default. 

thanks for the link, i'll trying when i get home!

---

### Post by chikko on 2007-02-09
> **robenroute said:**
> See [here]("http://ubuntuforums.org/showthread.php?t=344839"). I hope that helps.

thanks a lot!!!  exactly what i was looking for! :)

---

