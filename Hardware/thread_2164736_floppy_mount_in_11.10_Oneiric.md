---
title: "floppy mount in 11.10 Oneiric"
date: 2013-08-01
forum: Hardware
---

### Post by Bunny Boy on 2013-08-01
I need to recover some files from an old floppy, but so far I haven't been able to access them.  

When I run

```
sudo fsck -t vfat /dev/fd0
```

it tells me that there are 22 files.

Then I run

```
sudo mount /dev/fd0 /mnt/floppy -t vfat
```

to mount it, but when I go to /mnt/floppy *ls* shows me nothing. 

Any idea what I'm doing wrong?

---

### Post by ajgreeny on 2013-08-01
I believe you need to use udisks now to mount a floppy, but I can't remember the command I used to use when I had a floppy to mount; I'll keep looking for you.

OK:  try this:-
```
udisks --mount /dev/fd0
``` and the same syntax to unmount, but with --umount, of course.  That worked for me in 10.04.

---

### Post by Bunny Boy on 2013-08-01
> **ajgreeny said:**
> I believe you need to use udisks now to mount a floppy, but I can't remember the command I used to use when I had a floppy to mount; I'll keep looking for you.

OK:  try this:-
```
udisks --mount /dev/fd0
``` and the same syntax to unmount, but with --umount, of course.  That worked for me in 10.04.

Thanks, *udisks* worked to mount it, and I was able to see the files.  Unfortunately, there's a problem with the --unmount command.  (the help says it's actually --unmount, not --umount).  When I try to unmount it so I can check another disk, I get this error message:

[B]Unmount failed: Cannot unmount because file system on device is busy
[/B]
Any ideas?

---

### Post by ajgreeny on 2013-08-02
Sorry about the unmount mistake; I'm so used to normally using umount that I assumed it was the same in this case for udisks.

Does the error when unmounting mention tumblerd, as happens sometimes when using USB drives with photos on them, eg a photo memory-card from a camera?  I use command **pkill tumblerd** when that happens and can then unmount and remove it safely.

---

