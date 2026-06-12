---
title: "overwriting a partition?"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by Hybrid86 on 2009-01-05
My laptop is partitioned into two partitions. One has kubuntu  8.04 on it. the other is an installation of 8.10, that I did to see if I liked kde 4 enough to make the switch yet. I am currently attempting to install ubuntu studio on the 8.10 partition, but have run into a problem. when in the ubuntu studio installer, I am unable to tell which partition is which. On is a labeled "#1", the other is "#6". There doesn't seem to be any way to differentiate between the two. I guess I'm new at this.

Does anyone know how I'm supposed to tell them apart?

---

### Post by 2hot6ft2 on 2009-01-05
You could look at the menu.lst to see which is which
it's in /boot/grub/menu.lst

---

### Post by Hybrid86 on 2009-01-05
Checked. It doesn't say which is which.

---

### Post by taurus on 2009-01-05
Since you want to keep hardy, boot into hardy and at the prompt, look at the harddrive layout/table to see which partition hardy is using as /.  Then, the other one should be your intrepid.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

