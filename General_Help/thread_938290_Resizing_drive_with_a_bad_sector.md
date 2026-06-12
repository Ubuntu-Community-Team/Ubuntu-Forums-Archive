---
title: "Resizing drive with a bad sector"
date: 2008-10-04
forum: General Help
---

### Post by Metaphysicist on 2008-10-04
I'm trying to resize my partition to later dual boot Ubuntu and Windows XP, but I have a bad sector. As you can see I have no idea how to use the ntfsclone --rescue command(picture below).

[IMG]http://img371.imageshack.us/img371/6798/rinuxjv4.png[/IMG]

---

### Post by pdwerryhouse on 2008-10-04
You probably want to do:

```
ntfsclone -o /var/tmp/backup.ntfs --rescue /dev/sda1
```

Substitute "/var/tmp/backup.ntfs" with the path to the file where you want to save the backed-up data.

---

### Post by Metaphysicist on 2008-10-04
I've just finished the chkdsk and am back in linux, would this command work to resize my current partition; to create a new partition in the free space and install linux?

```
ntfsresize -b -s 160G
```

---

### Post by Metaphysicist on 2008-10-05
> **Metaphysicist said:**
> I've just finished the chkdsk and am back in linux, would this command work to resize my current partition; to create a new partition in the free space and install linux?



Doesn't work, does anyone know what the command should look like?

---

### Post by Metaphysicist on 2008-10-05
bump?

---

### Post by caljohnsmith on 2008-10-05
Have you run a "chkdsk /r" on your NTFS partition like gparted suggested? You can do that from a Windows Install CD by typing "r" at the first main menu to get the recovery console, and then running it:
```
chkdsk /r
```
When you say that ntfsresize command "doesn't work", what happens? Also, I noticed in the ntfsresize manual:
> **Shrinkage**
If you wish to shrink an NTFS partition, first use ntfsresize to shrink the  size  of the filesystem. Then you could use fdisk( 8 ) to shrink the size of the partition by deleting the partition and recreating it  with the  smaller size.  Do not make the partition smaller than the new size of NTFS otherwise you won&#8217;t be able to boot. If  you  did  so notwithstanding then just recreate the partition to be as large as NTFS.
So it looks like you may need fdisk to shrink the partition once you get ntfsresize to work.

---

