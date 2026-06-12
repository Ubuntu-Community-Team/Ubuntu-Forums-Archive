---
title: "Grub - File Not Found"
date: 2008-08-29
forum: General Help
---

### Post by TheForkOfJustice on 2008-08-29
Recently installed a kernel upgrade in Gutsy but I didn't reboot properly due to a freeze.  I can no longer boot that partition (other partitions work fine).

I used a correct menu.lst from the unaltered partition (but unbootable at the moment due to a menu.lst without the correct entries) using the livecd. However, I still cannot boot the partition that had its kernel updated.

GRUB seems to have all of the correct paths, UUIDs, etc. but keeps telling me 'File Not Found'.

Any ideas on how to fix?

---

### Post by spiderbatdad on 2008-08-29
do you dual boot with xp?
[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)
there are a lot of guides on how to fix grub using the live cd.

---

### Post by caljohnsmith on 2008-08-30
Is your Ubuntu partition mountable still? If not you could run an fsck on it to try and repair any file system problems. If it is mountable, then from the Live CD I would:
```
sudo mount /dev/[COLOR="Blue"]sdX[/COLOR] /mnt
ls -l /mnt/boot
cat /mnt/boot/grub/menu.lst
```
Where sdX is your Ubuntu partition. The above will list all the kernel files and such in your /boot directory as well as printing your menu.lst, and then you can compare the files in /boot with your menu.lst. If you need further help getting things working, please post the output of everything above as well as:
```
sudo fdisk -lu
```

---

### Post by TheForkOfJustice on 2008-08-30
Okay, I managed to fix GRUB and can 'boot' the partition I was having trouble with.

However, when it attempts to load it will fail.  I had the Gutsy package called 'preload' installed but it fails to load and nothing else loads afterwards.  It is supposed to load things faster but is being a bother now so is there a way to remove it or bypass it or something?

---

### Post by TheForkOfJustice on 2008-08-31
Can someone help me find a post/howto on how to chroot my other Ubuntu installation. I think that's how I can uninstall the problem package,

---

### Post by spiderbatdad on 2008-08-31
[https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)

---

