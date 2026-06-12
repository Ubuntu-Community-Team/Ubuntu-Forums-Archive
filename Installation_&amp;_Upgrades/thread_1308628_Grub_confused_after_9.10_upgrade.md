---
title: "Grub confused after 9.10 upgrade"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by arcoain on 2009-10-31
I recently upgraded to 9.10, and for some reason, kept telling Ubuntu to keep my old menu.lst (I am an idiot).  Anyway, now my menu.lst is trying to boot my into 9.04 (which of course doesn't really work), and I get to a nerfed (initramfs) command prompt (so I can't just run 'update-grub' to overwrite my menu.lst.  How can I fix this?
Thanks,
arcoain

---

### Post by lemming465 on 2009-11-01
If you have a live CD handy, try booting it, mount your root (and if necessary other filesystems, particularly /boot if that was separate) and do something like:```

sudo -i
mount /dev/sda2 /mnt # use whatever you root partition is
cd /mnt
for x in proc sys dev; do mount -o bind /$x $x; done
chroot .
update-grub
```

---

