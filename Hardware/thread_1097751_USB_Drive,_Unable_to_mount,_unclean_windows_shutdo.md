---
title: "USB Drive, Unable to mount, unclean windows shutdown"
date: 2009-03-16
forum: Hardware
---

### Post by diver boy on 2009-03-16
I just installed ubuntu studio after my hard drive, running windows XP, crashed.  I am ttempting to mout an external USB drive.  The system sees it, but will not mount, as it says :

$LogFile indicated unclean shutdown (0,0) Failed to mount '/dev/sdb1':  Operation not supported Mount is denied because NTFS is marked to be in use.

I no longer have a windows system to unmount it from, and when I try

sudo mount -t ntfs-3f /dev/sdb1 /media/New Volume -0 force

I get a listing of mount options.  What am I doing wrong?

---

### Post by Therion on 2009-03-16
Try this instead: ```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
```

(For one thing it's ntfs-3**g**, not **f**...)  ;)

Then, if it's still balking: ```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
```

---

### Post by diver boy on 2009-03-16
When I added the -o force option sat the end, it worked, thanks.

---

### Post by cholericfun on 2009-03-19
(too late now...)
just want to add that after such a warning,
removing the usb device and plugging it in again generally does the tick for me as well.

---

