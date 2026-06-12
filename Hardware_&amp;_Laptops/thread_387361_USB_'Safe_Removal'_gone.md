---
title: "USB 'Safe Removal' gone?"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by mertle on 2007-03-18
I use a 30 GB video iPod (with a broken screen) as an external HD to keep all my backups rsync'ed and all and seem to be having a problem safely ejecting it sometimes. Normally, when I right click on the iPod icon (or any USB device) on the desktop, it gives me the option to "Safely Remove". More often than not, after writing to the disk, I no longer have that option.

Is it safe to remove a USB device without 'Safely Remove'ing it? If not, what do I do when I don't have the option, simply 'umount /dev/sdb' it? I know back in Winblows there was an option to turn off disk caching so that you could use quick removal, but I dunno if (K)ubuntu has/needs something similar.

- mertle

EDIT: BTW, the iPod has been formatted FAT32 so I can use it both in Windows and Linux, if that makes any difference.

---

### Post by yabbadabbadont on 2007-03-18
As long as you unmount the partition first, you should be fine.  If you are really paranoid, run the "sync" command a couple of times before you unmount it.  (although umount should sync the drive before it unmounts the partition)

---

### Post by tacubuntuforums on 2007-03-18
In addition, very often you'll have to quit from the file browser application you were using to view the USB drive contents before being able to unmount.

I don't know why it continues to be like that, but it does.
Nautilus should accept also pasting and copying paths, to go quickly to folders/files, many times when it doesn't; it's impossiblet due to a limitation in the design of the application. In my opinion that's VERY important. Unfortunately the file browser in Xubuntu has the same absurd limitation.

---

