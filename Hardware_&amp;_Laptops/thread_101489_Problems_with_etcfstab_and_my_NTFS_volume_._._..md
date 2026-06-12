---
title: "Problems with /etc/fstab and my NTFS volume . . ."
date: 2005-12-09
forum: Hardware &amp; Laptops
---

### Post by Wilco on 2005-12-09
For some reason, I cannot get my NTFS drive to mount automatically during bootup. Once I'm logged in, I can manually mount it without any trouble - any ideas why this would be? (could it have something to do with the SATA interface its using?)

Here's the entry in my /etc/fstab
----------------------------------------------
/dev/sda1	/media/windows	ntfs		nls=utf8,umask=0222		0	0
----------------------------------------------

When I enter the command in manually, it works fine!
----------------------------------------------
mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
----------------------------------------------

Any idea what the problem is?

---

### Post by matthew on 2005-12-10
I'm not sure what the problem is, but the fstab entry looks correct. Strange.

Anyway, *bump* maybe someone else will notice and have an idea.

---

### Post by Wilco on 2005-12-10
Could it be that it attempts to mount the drive before any SATA drivers are loaded? It seems unlikely (being that controller drivers would be expected to load before any mounting attempts are made). Just some thougts . . .

---

### Post by Kurt Dodrill on 2005-12-14
Im kinda new to this myself...but don't you put auto as an option for the fstab entry?

---

