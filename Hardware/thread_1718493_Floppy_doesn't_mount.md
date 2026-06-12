---
title: "Floppy doesn't mount"
date: 2011-03-31
forum: Hardware
---

### Post by claus on 2011-03-31
Hi,

when trying to access an old floppy disk today, the floppy drive didn't mount. I purchased this (used) PC in late 2009, and so far, I didn't use the floppy drive, so I'm not quite sure if this is a hardware failure or if the problem is software related.

The floppy entry in '/etc/fstab' reads as follows:

/dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0

'/etc/modules' contains 'floppy'.

I tried 'sudo mount -t vfat /dev/fd0 /media/floppy', but to no avail. The LED on the floppy drive goes on, but the drive isn't mounted. Does anybody have some suggestion how I can solve this problem?

TIA,

Claus

---

### Post by Yellow Pasque on 2011-03-31
Thoughts :
- Use lsmod to make sure floppy module is loaded.
- Make sure floppy is enabled in BIOS/setup
- See if you can boot a bootable floppy (make sure it doesn't have a virus). You might even try a blank one to see if it reads properly.
- Look in dmesg for mount errors

---

### Post by SeijiSensei on 2011-03-31
Is the floppy formatted?  For a long time floppy disks were not formatted at the factory and you had to format them yourself.  If the floppy has data you need to read from the disk, don't do this as the contents of the disk will be deleted.

Try inserting the floppy into the drive, then run 

```
mkfs -t vfat /dev/fd0
```

You should see the light come on and the drive grind away for a while.  Eventually you'll get a confirmation that the drive is formatted.  Now try seeing if it mounts.  You might still need to use the "mount" command as you described in your post.

Oh, and make sure the little switch that write-protects the drive is unlocked.  It's in an upper corner of the floppy.

If the floppy is "too" old, it may simply not work any more.  If you can't format it, then it's probably out-of-service.

---

### Post by Morbius1 on 2011-03-31
Insert the floppy and run the following command:
```
udisks --mount /dev/fd0
```
You'll get an icon on the desktop labeled "floppy0"

Double click that and if there still any data on it you may get lucky :)

---

