---
title: "merge (photo) directories"
date: 2008-07-13
forum: General Help
---

### Post by masterdam79 on 2008-07-13
Hi there all,

I have two directories which I like to merge.
/media/disk/PHOTOS/Locations/
/media/disk/PHOTOS/Locations2/

In each of these directories there are subdirectories like /Netherlands/Amsterdam or /England/York

I've looked into the use of the 'diff' command which gives me the results of both directories and I've read about a 'merge' command which I could use in a pipe as something like:
```
diff /media/disk/PHOTOS/Locations/Netherlands/Amsterdam/ /media/disk/PHOTOS/Locations2/Netherlands/Amsterdam/
```
and then 
```
merge /media/disk/PHOTOS/Locations/Netherlands/Amsterdam/ /media/disk/PHOTOS/Locations2/Netherlands/Amsterdam/
```

Would anyone know how to go about this?

Much thanks

---

### Post by Afkpuz on 2008-07-15
Why not not open locations2, select all, and copy and paste into locations?  You can do this graphically.  Is there something I'm missing?

---

### Post by masterdam79 on 2008-07-18
The content of both directories are very different, but have similar filenames (as I recovered a drive theya re all called photo-001.jpg photo-002.jpg etc.)
I'm looking for a tool that will check filenames by hash or something like modification date and filesize and will make dir1 + dir2 = dir3 without doubles.

Cheers,

---

