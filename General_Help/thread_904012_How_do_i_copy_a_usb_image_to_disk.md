---
title: "How do i copy a usb image to disk?"
date: 2008-08-28
forum: General Help
---

### Post by rotteneggz on 2008-08-28
Hello all
I am the ultimate linux noob looking for some help.
I need to copy a usb image to the disk.
This is what i found from another site for copying a floppy image to the disk: dd if=/dev/fd0 of=dban-boot.img bs=10k count=144 
Now how would i do that but with a usb instead?
Thanks in advance

---

### Post by mssever on 2008-08-28
Replace /dev/fd0 with the name of your USB device, and adjust the bs and count parameters to reflect your USB device. See the dd man page for documentation on bs and count.

---

### Post by rotteneggz on 2008-08-28
hey thanks for the quick reply.
How do i check the name of my usb device?

---

### Post by mssever on 2008-08-28
> **rotteneggz said:**
> hey thanks for the quick reply.
How do i check the name of my usb device?
Type mount and you'll see the device name and the mount point.

---

