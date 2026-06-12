---
title: "Efidisk write error after clean installation on SSD"
date: 2013-04-13
forum: Hardware
---

### Post by stilllife on 2013-04-13
Hi all, I just bought a new SSD and installed on it xubuntu 12.04. Everything works fine but right after the grub menu the monitor stays black for some second and the I get:

efidisk write error
Please any key to continue....

If I press a button the system load without any problem

Any idea on how can I fix that error?

This is my fstab
```

# / was on /dev/sda3 during installation
UUID=966de96e-9fc8-4c59-9dce-5d05dec95c85 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=2BCD-0B79  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda4 during installation
UUID=3aa7498b-32cc-46e2-bbec-ee2287341210 none            swap    sw              0       0

```

---

