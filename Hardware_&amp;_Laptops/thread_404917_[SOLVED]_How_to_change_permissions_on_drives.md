---
title: "[SOLVED] How to change permissions on drives?"
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by brion@cbkidder.com on 2007-04-09
Although I am able to mount both my external USB-hard drive (BACKUP) and my internal 2nd hard drive (Reference) via /media/BACKUP and /media/Reference, neither allows me to add or delete files & folders.

When I try to change the external HD permissions via the GUI, I get the error
[CENTER]"The permissions could not be changed. Couldn't change the permissions of "BACKUP" because it is on a read-only disk."[/CENTER]

When I try to change the internal 2nd HD permissions I am locked out, with the message "You are not the owner, so you can't change these permissions."

I am the only user of this machine, so what do I need to do so I can read and write, create and delete files and folders on these drives?

---

### Post by heimo on 2007-04-09
Check if this answers your question:
[https://help.ubuntu.com/community/VolumePermissions](https://help.ubuntu.com/community/VolumePermissions)

---

### Post by lukew on 2007-04-09
> **brion@cbkidder.com said:**
> Although I am able to mount both my external USB-hard drive (BACKUP) and my internal 2nd hard drive (Reference) via /media/BACKUP and /media/Reference, neither allows me to add or delete files & folders.

When I try to change the external HD permissions via the GUI, I get the error
[CENTER]"The permissions could not be changed. Couldn't change the permissions of "BACKUP" because it is on a read-only disk."[/CENTER]

When I try to change the internal 2nd HD permissions I am locked out, with the message "You are not the owner, so you can't change these permissions."

I am the only user of this machine, so what do I need to do so I can read and write, create and delete files and folders on these drives?

What is the format of the drive?  Ifyou have ro options on the fstab you might have errors and might need to run fsck to fix them. ro means turn readonly when you have errors.

Luke

---

### Post by brion@cbkidder.com on 2007-04-10
Heimo, thanks for the link. I was able to copy folders and files to the "Reference" drive but strangely I still am not able to create new folders using the right-click context-sensitive menu. I have to create a folder on my desktop and drag it in, which is odd, but fine since I mostly use "Reference" as a file archive that I back up to external HDD "BACKUP" every month.

---

### Post by brion@cbkidder.com on 2007-04-10
Hi Luke, thanks for the suggestions. The internal 2nd HD is FAT32, and appears in fstab as

/dev/hdb1       /media/Reference     vfat umask=000 0 0

as per Heimo's link above. I have read-write ability via drag-and-drop but strangely I cannot create folders directly in the drive. Weird. Maybe I need to do a completely cold reboot...

---

### Post by brion@cbkidder.com on 2007-04-10
Confirmed. I needed to do a completely cold reboot after changing the fstab and re-mounting the drives for the permissions to appear in the context-sensitive menus.
Thanks again!

Registered Linux User #446294 @ Linux Counter, [http://counter.li.org]("http://counter.li.org").

---

