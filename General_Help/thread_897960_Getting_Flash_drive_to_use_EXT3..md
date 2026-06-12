---
title: "Getting Flash drive to use EXT3."
date: 2008-08-22
forum: General Help
---

### Post by MechWarrior001 on 2008-08-22
Does anyone know how to get my flash drive to use EXT3 and be recognizable by windows? Would it be worth it?

---

### Post by LateNiteTV on 2008-08-22
you can format it to ext3 by:
```

mkfs /dev/FlashDeviceName
```

im not too sure if windows can read ext3... but you can format it to FAT which is readable and writeable by both linux and windows:
```

mkfs -t vfat /dev/FlashDeviceName
```

why do you want it formatted as ext3?

---

### Post by MechWarrior001 on 2008-08-22
I'm getting tired of fragmentation.

---

### Post by LateNiteTV on 2008-08-22
ah yes, i dont blame you. but windows CANT read or write to ext3. just confirmed by one of my coworkers.

---

### Post by SkonesMickLoud on 2008-08-22
There are programs that you can install to Windows that will allow it to read and possibly write to ext3.

This allows read-only:
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

Read-only also:
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

This can read/write, but only to ext2:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

The last one is probably your best bet, but from a cursory look at the site it looks like the flash drive will have to be ext2.  Something about the journaling of ext3 conflicting.

---

### Post by my_key on 2008-08-22
You can use [ext2 ifs]("http://www.fs-driver.org/") to read and write to ext3 from windows.

If you just need to read ext3 in win try: [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm) (no need to install it, just run the exe). The new version can read-write but is still in beta, can be found on: [http://www.chrysocome.net/virtualvolumes](http://www.chrysocome.net/virtualvolumes)

Cheers

edit: SkonesMickLoud, you beat me to it :)

---

### Post by jimv on 2008-08-22
Install this driver on your windows machine and it will be able to read/write Ext3:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by my_key on 2008-08-22
> **SkonesMickLoud said:**
> This can read/write, but only to ext2:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

The last one is probably your best bet, but from a cursory look at the site it looks like the flash drive will have to be ext2.  Something about the journaling of ext3 conflicting.

Not really true. I've been using this to mount ext3 for a while in win32 systems and it works like a charm. I refer to their FAQ: [http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3)

---

### Post by SkonesMickLoud on 2008-08-22
> **my_key said:**
> Not really true. I've been using this to mount ext3 for a while in win32 systems and it works like a charm. I refer to their FAQ: [http://www.fs-driver.org/faq.html#acc_ext3](http://www.fs-driver.org/faq.html#acc_ext3)


Yeah, I gave their site a very cursory glance.  Protip to self:  "Don't skim and then try to sound like you know what you're talking about."

:lolflag:

---

