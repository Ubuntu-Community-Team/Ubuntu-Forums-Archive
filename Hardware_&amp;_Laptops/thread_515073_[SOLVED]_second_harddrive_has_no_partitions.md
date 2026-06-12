---
title: "[SOLVED] second harddrive has no partitions"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by scragar on 2007-08-01
I recently installed a second harddrive, but now in disks it shows up as being attached:
[http://i37.photobucket.com/albums/e66/scragar/2disks.png](http://i37.photobucket.com/albums/e66/scragar/2disks.png)
but when I click it I get told that the partition doesn't have any partions:
[http://i37.photobucket.com/albums/e66/scragar/nopartions.png](http://i37.photobucket.com/albums/e66/scragar/nopartions.png)
is there any way I can add partitions to this hd?
or even just reformat it(it's empty at the mo, so no loss)

---

### Post by hysteresis on 2007-08-01
sudo fdisk /dev/hdb?

---

### Post by scragar on 2007-08-01
that was exactly what I needed,

it's up and running now.

thanks again.

---

