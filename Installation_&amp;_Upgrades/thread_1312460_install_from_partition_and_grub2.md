---
title: "install from partition and grub2"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by kabanta on 2009-11-03
has anyone who is using grub2 tried installing additional operating systems *from a partition*?

the information relevant to grub2 has not been updated here:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

specifically, this information is specific to legacy grub (and /boot/grub/menu.lst):

```

title           installer
root            (hd0,0)
kernel          /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd          /casper/initrd.gz
```

for grub2, i believe it needs to be something like this (in /etc/grub.d/40_custom):

```

menuentry "installer on sda1" {
    set root=(hd0,1)
    linux /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
    initrd  /casper/initrd.gz
}
```

followed by: **update-grub**

however, i am concerned that if this is not correct, the installation process may bork the startup menu and access to the different installations.

anyone had experience with this yet?

---

