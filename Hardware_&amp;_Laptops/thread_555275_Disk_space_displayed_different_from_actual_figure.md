---
title: "Disk space displayed different from actual figure"
date: 2007-09-19
forum: Hardware &amp; Laptops
---

### Post by jnbptst on 2007-09-19
Hi,

I run Ubuntu 7.04 on my IBM laptop, with a Windows XP Dual Boot.

I have a 240Gb external hard drive that I use to store files. It used to be almost full so I made some free space on it by deleting files while I was running my computer on a Windows XP session.

Now when I run on Linux it still pretends the hard drive is full (under Windows it's OK and the actual free space is displayed).

A small screenshot is better than a long post:

[[IMG]http://img527.imageshack.us/img527/3370/wrongdiskspacers2.th.png[/IMG]](http://img527.imageshack.us/my.php?image=wrongdiskspacers2.png)

As you may see, when I analyse the /media/disk folder (my external hard drive), it displays the correct amount on actual data on it (170,5Gb) and the correct total size of the hard drive (240,6Gb); however, the disk appears almost full (on top: "utilisé" - used : 238,8Gb).

70Gb disappeared in limbo and I can't write anything on the drive!

What should I do?

Thanks in advance for the help

---

### Post by dcstar on 2007-09-20
> **jnbptst said:**
> Hi,

I run Ubuntu 7.04 on my IBM laptop, with a Windows XP Dual Boot.

I have a 240Gb external hard drive that I use to store files. It used to be almost full so I made some free space on it by deleting files while I was running my computer on a Windows XP session.
.........

Were the files actually deleted or just put into the trash?

There is a known bug where files that are required by the system are "hidden" from the disk space calculations, even though they actually do exist on the filesystem.

---

### Post by jnbptst on 2007-09-20
my windows trash is empty so i guess the files are supposed to be deleted definitely

---

### Post by dcstar on 2007-09-21
> **jnbptst said:**
> Hi,

I run Ubuntu 7.04 on my IBM laptop, with a Windows XP Dual Boot.
.......
70Gb disappeared in limbo and I **can't write** anything on the drive!

What should I do?

Thanks in advance for the help

If it is a NTFS filesystem, then I assume you mount it using the ntfs-3g so you actually have write access to it, otherwise you will have NO "free space" to write even if it was totally empty!

---

### Post by jnbptst on 2007-09-21
Sorry, forgot to mention that: it is a FAT 32 system

---

