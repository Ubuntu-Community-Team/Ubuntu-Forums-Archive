---
title: "Unable to use floppy drive - /dev/fd0 nonexistent"
date: 2009-05-05
forum: Hardware
---

### Post by Darael on 2009-05-05
I've recently added an old floppy drive to an existing install (jaunty), but even though I've made sure the kernel module is loaded, the system doesn't recognise the drive's existence.  This means it doesn't appear in the "computer" nautilus location, or anywhere else for that matter.  I've tried issuing "ls -l /dev | grep fd" and I get only:
```
lrwxrwxrwx  1 root   root          13 2009-05-05 22:47 fd -> /proc/self/fd
lrwxrwxrwx  1 root   root          15 2009-05-05 22:47 stderr -> /proc/self/fd/2
lrwxrwxrwx  1 root   root          15 2009-05-05 22:47 stdin -> /proc/self/fd/0
lrwxrwxrwx  1 root   root          15 2009-05-05 22:47 stdout -> /proc/self/fd/1
```
which obviously means /dev/fd0 does not exist.

Any ideas?

---

### Post by jerrrys on 2009-05-05
take a step back...can bios see your floppy?

should also say that i run 804, can't tell you if 904 even supports a floppy...

---

### Post by Darael on 2009-05-06
I did think about whether my BIOS supports a floppy drive, but there are several options in there regarding one, so I assumed it must do.

I remembered this morning, though, that a setting for "A drive type" or something similar had been set to none - changing it to "1.44, 3.5in" means that my drive is now recognised as existing, though I still can't mount the disks and the activity led is permanently on.

---

