---
title: "Fixing hibernation on a Lenovo v100"
date: 2008-10-22
forum: Hardware
---

### Post by cmavr8 on 2008-10-22
Hello, hibernating and suspend to ram does not work any more in my laptop.

I think I need to re-set the uuids, because my swap partition changed uuid.

So, I updated these files:
```
/etc/fstab
/etc/initramfs-tools/conf.d
```

to show my new swap's uuid.

Now I try sudo dpkg-reconfigure  initramfs-tools and I get:
```
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic
readlink: No such file or directory
cpio: not implemented or invalid option --
/usr/sbin/mkinitramfs: 279: cannot create : Directory nonexistent
update-initramfs: failed for /boot/initrd.img-2.6.24-21-generic
```

Any help?
Thanks

---

