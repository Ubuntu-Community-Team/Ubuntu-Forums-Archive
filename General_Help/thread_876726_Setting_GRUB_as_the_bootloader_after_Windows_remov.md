---
title: "Setting GRUB as the bootloader after Windows removes it"
date: 2008-08-01
forum: General Help
---

### Post by Zoasterboy on 2008-08-01
I need to reinstall windows on my machine, as it killed itself somehow. (Ubuntu is doing fine, of course). My question is, how do I reinstate GRUB as the default boot loader after installing Windows?

---

### Post by primolarry on 2008-08-01
Well there probably is a better and faster way to do it, but I have always done it this way:

-Boot from a Live CD
-Mount your linux partition in (for example) /mnt/linux
-Mount your dev and proc:

```

mount -o bind /dev /mnt/linux/dev
mount -o bind /proc /mnt/linux/proc

```

-Perform chroot
```

chroot /mnt/linux /bin/bash

```

-Load your profile
```

source /etc/profile

```

-And finally you rebuild grub. Assuming your disk is /dev/sda.
```

grub-install /dev/sda

```

Regards

---

### Post by prshah on 2008-08-01
> **Zoasterboy said:**
> I need to reinstall windows on my machine, My question is, how do I reinstate GRUB as the default boot loader after 

You'll most likely need the live CD for this:

Before you install Windows, create a backup copy of your MBR by ```

sudo dd if=/dev/sdx of=/root/orig.mbr bs=512 count=1
``` 

This is the backup of your MBR. Copy this to a USB pendrive or some other device. Restore it after installing Windows using the live CD and the command```

sudo dd if=/location/orig.mbr of=/dev/sdx bs=512 count=1
```

Replace sdx with the actual device name, and "location" with the path to the orig.mbr file.

Note that if you're going to make partition changes, you should backup/restore only the first 446 bytes (bs=446). Also remember that if you make partition changes, you will need to have those changes reflected in your /boot/grub/menu.lst.

Make sure "Boot sector write protect" BIOS option is turned off.

Be very very careful with the dd command; a single added/misplaced numeral can destroy your data in a second.

---

### Post by Rocket2DMn on 2008-08-01
Whoa, there are much easier ways to do this!
First, check out [uhelp]community/RecoveringUbuntuAfterInstallingWindows[/uhelp]
The simplest way is to use the Super Grub Disk - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) - which can just reinstall GRUB for you.

---

### Post by Zoasterboy on 2008-08-01
Cool, thanks for the help!

---

