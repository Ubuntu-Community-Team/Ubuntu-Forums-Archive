---
title: "GRUB error while upgrading from ext3 to ext4"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by BuntuFirstTimer on 2009-05-22
I just installed Ubuntu 9.04.

I used this guideline to start upgrading the file system.

[http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)

When I typed this code: ```
sudo mount -t ext4 /dev/XXXX /mnt
```

It gives me a weird feedback. It brought me **/dev/sda1: Group descriptor **** checksum is invalid.  FIXED.** and a long delay.

Then, when I typed ```
sudo grub-install /dev/sda
``` from the guide above, I got: **Could not find device for /boot: Not found or not a block device.**

Overall I think I did something very wrong how to upgrade from ext3 to ext4.

Any help from this? Thanks in advance.

---

