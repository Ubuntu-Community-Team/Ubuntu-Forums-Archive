---
title: "Virtual Filesystem In RAM"
date: 2008-07-10
forum: General Help
---

### Post by solarwind on 2008-07-10
Is there a way to make a virtual filesystem in RAM? For example, is there a way to make a device called /dev/my_ram_disk that is 1 GB big and format it with JFS for example?

---

### Post by kerry_s on 2008-07-10
[http://www.vanemery.com/Linux/Ramdisk/ramdisk.html](http://www.vanemery.com/Linux/Ramdisk/ramdisk.html)

---

### Post by solarwind on 2008-07-10
> **kerry_s said:**
> [http://www.vanemery.com/Linux/Ramdisk/ramdisk.html](http://www.vanemery.com/Linux/Ramdisk/ramdisk.html)

Thanks, but how do I make my own ramdisk of lets say... 512 MB?

---

### Post by sdennie on 2008-07-10
Is there a particular reason you want to do this?  If you have enough RAM, over time, you will essentially create an on the fly RAM-disk via the filesystem cache.  It will take longer for it to come into existence but, it's usually more efficient than creating a full RAM-disk.

---

### Post by kerry_s on 2008-07-10
all the instructions are there, just add "ramdisk_size=524288" to /boot/grub/menu.lst

524288=512x1024

then after you reboot:

```
mke2fs -m 0 /dev/ram0
mkdir /mnt/rd
mount /dev/ram0 /mnt/rd

```

---

### Post by solarwind on 2008-07-11
> **vor said:**
> Is there a particular reason you want to do this?  If you have enough RAM, over time, you will essentially create an on the fly RAM-disk via the filesystem cache.  It will take longer for it to come into existence but, it's usually more efficient than creating a full RAM-disk.

Yes there is a particular reason.

---

