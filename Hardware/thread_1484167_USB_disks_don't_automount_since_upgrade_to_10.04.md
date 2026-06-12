---
title: "USB disks don't automount since upgrade to 10.04"
date: 2010-05-15
forum: Hardware
---

### Post by erikla2002 on 2010-05-15
I recently upgraded to 10.4 from 9.10 and since the upgrade my usb sticks won't automount if I plug in them. My android sd card for example, always appeared under Places when I inserted it. Now I can see it if I sudo fdisk -l and I can mount it with mount /dev/sdf1 /mountpoint etc but I dont wanna do that every time.

---

### Post by camdude on 2010-05-15
:confused: thats odd... I'm able to just plug in my thumb drives and it will work... It might be that your filesystem on your thumb drive isn't fully supported. What type of filesystem are you using?

---

### Post by erikla2002 on 2010-05-16
Its FAT32 and the exact same filesystem automounted just fine before the upgrade.

EDIT: I tried to mount right now and this time it worked. Weird.

---

