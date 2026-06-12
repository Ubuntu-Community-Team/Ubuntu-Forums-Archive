---
title: "Combining Partitions"
date: 2008-09-07
forum: General Help
---

### Post by Killtodie on 2008-09-07
So I had ubuntu on dual boot. I deleted the NTFS partition and formated it to ex2

how can I combine it to my existing extended partition?
here is how it looks now.
[IMG]http://img56.imageshack.us/my.php?image=screenshotdz9.jpg[/IMG]

image aint showing up? here is direct link
[http://img56.imageshack.us/my.php?image=screenshotdz9.jpg](http://img56.imageshack.us/my.php?image=screenshotdz9.jpg)

---

### Post by tuxulin on 2008-09-07
deleted
Tuxulin

---

### Post by -Zeus- on 2008-09-07
delete the ext2 partition, resize the extended partition, then resize the ext3 partition.

---

### Post by Killtodie on 2008-09-07
i cant resize it

---

### Post by -Zeus- on 2008-09-07
> **Killtodie said:**
> i cant resize it

you need to boot to the live cd and use gparted on there.  you can't resize it cause it's mounted.

---

### Post by Killtodie on 2008-09-07
oh, I can only do it of the CD. cause I installed gparted.

ok, so now it lets me resize the ext 3 part but not the extended part but I cant make it bigger, only smaller


nm, got it. swap remained mounted for some reason

---

### Post by -Zeus- on 2008-09-07
could you mark the thread solved please?

---

### Post by Killtodie on 2008-09-07
not yet.

how do i make grub go away. it still loads

---

### Post by -Zeus- on 2008-09-07
of course it loads.  you still need that to make a kernel selection/boot in recovery mode.  the presence of GRUB has nothing to do with a dual-boot.

---

### Post by Killtodie on 2008-09-07
my laptop has just ubuntu i never see grub load. this gives me the 8 second option and still lists xp. how can i edit this?

---

### Post by -Zeus- on 2008-09-07
i'm guessing that you have the hidden menu enabled?  go to your /boot/grub/menu.lst and change #hiddenmenu to hiddenmenu

Also change the line timeout 8 to timeout 1 or however many seconds you want it to wait.

---

### Post by Killtodie on 2008-09-07
tells me I dont have permissions to save

---

