---
title: "Removing corrupted filesystem entry"
date: 2008-10-27
forum: General Help
---

### Post by supernovus on 2008-10-27
So, I am using rsnapshot to back up a bunch of stuff, and I noticed that the weekly snapshots weren't rotating properly. Then I noticed that when rsnapshot had tried to remove the weekly.3 directory, it wasn't being removed.

I tried removing it myself with a "sudo rm -rf weekly.3" and it didn't do anything. So I looked inside it and found an .svn folder with what looked like a directory called "props" but which apparently doesn't exist.

```
tim@timt-w:/storage/backup/weekly.3/server/.svn$ ls -lah
ls: cannot access props: No such file or directory
total 8.0K
drwxr-xr-x 3 tim tim 4.0K 2008-10-20 03:04 .
drwxr-xr-x 3 tim tim 4.0K 2008-10-20 03:04 ..
d????????? ? ?   ?      ?                ? props
tim@timt-w:/storage/backup/weekly.3/server/.svn$

```

There does not appear to be any way of removing it. I was able to move the weekly.3 folder off into another directory inside the /storage drive, so I can get my rsnapshot rotations working again, but I can't apparently remove the props directory, as it doesn't exist.

Any ideas for how to actually get this corrupted entry to go away?

---

### Post by dcstar on 2008-10-28
> **supernovus said:**
> 
........
Any ideas for how to actually get this corrupted entry to go away?

fsck should be run on the partition (which has to be unmounted).

Just because you can't delete a corrupted entry does not mean that it is not actually there, the name could contain un-displayable characters that you do not end up typing so you can never get an exact match.

Use the following command which will prompt you to delete each thing it finds - but be VERY careful with it and CTRL/C out of it when you have deleted the one you want:

```
rm -i -R *
```

---

### Post by supernovus on 2008-10-28
> **dcstar said:**
> fsck should be run on the partition (which has to be unmounted).

Just because you can't delete a corrupted entry does not mean that it is not actually there, the name could contain un-displayable characters that you do not end up typing so you can never get an exact match.

Use the following command which will prompt you to delete each thing it finds - but be VERY careful with it and CTRL/C out of it when you have deleted the one you want:

```
rm -i -R *
```

Unfortunately, no, the entry is corrupted in the filesystem tables itself. It's not a case of invalid characters. Even 'ls' breaks on trying to list the file. I'm going to fsck the partition at some point, until then I'm just ignoring it. In 13 years of using GNU/Linux, this is the first time I've come across such a nice case of corruption.

Anyway, just wondering if anyone else has seen something corrupted so, where all of the properties of the entry are shown as question marks.

It may be a symptom of physical corruption on the harddrive. Fun stuff!

---

