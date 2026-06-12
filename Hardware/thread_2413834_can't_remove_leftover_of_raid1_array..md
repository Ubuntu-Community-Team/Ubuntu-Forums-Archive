---
title: "can't remove leftover of raid1 array."
date: 2019-03-02
forum: Hardware
---

### Post by astrogator2 on 2019-03-02
I am desperately trying to remove sda6, the leftover half of md1, my old homefolder from a previous installation.  I have already managed to mount it and get the data out but now I want to remove it so I can reconfigure that hd, the room it takes up is needed to expand another partition.  I have tried to remove its raid status in console, but it keeps on appearing as an extra md1 disk in gparted.  Even though both md1 and sda6 have been unmounted I cannot remove either, the option is greyed out in Gparted, and using commands in console returns a device busy, even though I have rebooted several times.

---

