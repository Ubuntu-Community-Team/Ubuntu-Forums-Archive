---
title: "boot image to floppy"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by meg23 on 2009-05-20
I am trying to install a boot image to a floppy attached through a usb external floppy drive. I cannot get the boot floppy properly imaged using the dd command. Please take a look at the output of these commands.

```

sudo dd if=boot.flp of=/dev/sdb 
2880+0 records in
2880+0 records out
1474560 bytes (1.5 MB) copied, 0.0427927 s, 34.5 MB/s
```

```
fdisk /dev/sdbYou will not be able to write the partition table.
This disk has both DOS and BSD magic.
Give the 'b' command to go to BSD mode.
You must set cylinders.
You can do this from the extra functions menu.

```

Thanks, Max

---

### Post by meg23 on 2009-05-20
and this:
```

sudo dd if=boot.flp of=/dev/sdb bs=1440k
1+0 records in
1+0 records out
1474560 bytes (1.5 MB) copied, 0.01727 s, 85.4 MB/s
```

---

