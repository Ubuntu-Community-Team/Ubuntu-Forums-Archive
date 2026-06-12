---
title: "Unable to format MicroSD card"
date: 2007-03-20
forum: Hardware &amp; Laptops
---

### Post by AngryGnome on 2007-03-20
Hello again,

I'm having trouble formatting a Kingston 1GB MicroSD card using gparted.  When I go into gparted it shows a lock next to the SD card's lable (Partition: /dev/sda1, Filesystem: fat16, Mountpoint /media/usbdisk) which I assume means that I do not have the proper permissions.  I have searched the forums and have been unable to find a way to change the permissions on the card so that I can format it.  (Sorry... new-ish to linux.)

Any help would be appreciated.

---

### Post by apjone on 2007-03-20
You need to unmount a file system before you can format it

---

### Post by AngryGnome on 2007-03-21
Ok... I get what you're saying... but now I have another problem.

When I go to format my MicroSD card with gparted I do this:

1. unmount
2. delete > apply (it then shows the microsd as unallocated space.)
3.  New > Primary Partition, FAT16, Free Space Preceding: 0, New Size: 981MB, Free Space Following: 0, Round to cylinders checked
4. Add

Then the MicroSD mounts itself as 'usbdisk' and I get this message from gparted: 

```
mkdosfs: /dev/sdb1 contains a mounted file system
```

Thus it won't format.

I really need help with this

---

### Post by apjone on 2007-03-21
open a terminal
```

sudo -s
enter password:xxxxxxxxxxxx
umount /dev/sda1
mkfs.msdos -F16 /dev/sda1
mount /dev/sda1 /media/usbdisk
exit
exit

```

That should format it and mount it

---

### Post by AngryGnome on 2007-03-21
Thanks very much... worked like a charm. :)

---

