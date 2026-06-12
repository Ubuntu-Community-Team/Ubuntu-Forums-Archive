---
title: "floppy mount"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by curt on 2005-07-19
I have checked in fstab. Floppy is there.
I have mounted the floppy using the GUI and CLI.
Each time I get:

"Unable to mount the Selected volume. mount: I could not determine the filesystem type, and none was specified"

The floppy drive will not read a formatted floppy of any kind.

Any help is appreciated ;-)

---

### Post by oxman on 2005-07-22
Friends, curt is an acquaintance of mine who is very interested in linux. I installed ubuntu on his computer ( I am a fedora core user). Please reply to this thread. He does not have access to his floppy drive from disks made from linux distros. What is the problem?

---

### Post by black hole sun on 2005-07-22
[QUOTE=oxman]Friends, curt is an acquaintance of mine who is very interested in linux. I installed ubuntu on his computer ( I am a fedora core user). Please reply to this thread. He does not have access to his floppy drive from disks made from linux distros. What is the problem?[/QUOTE]
 Well, tell your friend to post his /etc/fstab file. I helped another new linux user with the same problem, it was a simple matter of changing the fs type to vfat...

---

### Post by oxman on 2005-07-22
black hole sun, thanks for the reply. I'm not at his house right now but I'll post it some time today.

I've never come up against this in any other linux distro. Shouldn't

```

mount /mnt/floppy

```

or 

```

mount /media/floppy

```

mount any IBM formatted floppy disc? I don't understand the problem.

---

### Post by black hole sun on 2005-07-22
[QUOTE=oxman]black hole sun, thanks for the reply. I'm not at his house right now but I'll post it some time today.

I've never come up against this in any other linux distro. Shouldn't

```

mount /mnt/floppy

```

or 

```

mount /media/floppy

```

mount any IBM formatted floppy disc? I don't understand the problem.[/QUOTE]
 What happens is mount tries to autodetect the filesystem used on the floppy and fails. I'm not really sure why, though, but the only sure-fire way to get a floppy mounted is to explicitly define its filesystem type, which is almost always FAT (FAT, FAT16, and FAT32 are all managed under the same unix driver, "vfat")

---

### Post by oxman on 2005-07-23
Thanks for the feedback. I'm heading over to his place today and will vim edit the fstab.

---

### Post by curt on 2005-07-23
[QUOTE=oxman]Thanks for the feedback. I'm heading over to his place today and will vim edit the fstab.[/QUOTE]
 black hole sun, thanks again. I'm at curt's place right now and the fstab edit worked like a charm.

---

