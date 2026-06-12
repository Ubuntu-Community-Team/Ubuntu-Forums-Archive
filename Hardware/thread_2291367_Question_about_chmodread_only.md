---
title: "Question about chmod/read only"
date: 2015-08-19
forum: Hardware
---

### Post by wjbmd48 on 2015-08-19
Hi:

I have a media player that from time to time decides that it's read only.

I've read up on the chmod command and have to admit I can't fathom how to apply it to an entire flash/USB drive, which is what the thing looks like to my system. (Lubuntu 14.04.1 LTS)

Say the thing is /media/bill/D188-8FC21

What's the terminal command to restore it to read and write (and delete, which is what I really want to do)?

Is there an easier way to do this besides terminal? (I've seen mention that this can be done in Accessories/Disk Manager, but can't see how to do that either.)


Thanks!

Bill

---

### Post by TheFu on 2015-08-19
Usually, when an entire disk becomes read-only it is a cable or connection issue. Reseat the device.

The chmod command will not help with NTFS or FAT32 or FAT16 or xFAT formated storage. It has ZERO effect on those. The permissions are controlled at mount time.

To fix - eject it, reseat the connection and hopefully it will mount read-write again.

Does that make sense and seem the likely cause in your situation?

---

### Post by wjbmd48 on 2015-08-19
Nope, not that easy.

What I usually wind up doing is saving the files and reformatting it.  I'm looking for something easier than that.

Thanks!

Bill

---

### Post by TheFu on 2015-08-20
Do you always **umount** (or eject) the storage before removing it from the system? If not, corruption can happen.

---

### Post by wjbmd48 on 2015-08-20
Aha, I do not, have to admit that I just yank 'em.

OK, I'll try to be a good boy and always eject first.

Thanks for all your help,

Bill

---

