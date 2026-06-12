---
title: "mp4 player formatting woes"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by Nikusan on 2007-06-24
Hi all,

I've got an generic inki1 mp4 player here. After an unsafe unmount it started reporting Read-only file system errors when I tried to create/delete/rename/etc the files on it. It has a 2GB fat16 partition. The gist I got from the web was to reformat it. 

I did a:
```
mkdosfs -F16 -v /dev/sdb1
```

The partition now mounts and unmounts fine and I can read and write files.

The problem is the device itself can't see the disk anymore. It keeps reporting "Empty disk!". I've seen this before with another generic mp3 player. Tell me there's a way to fix this?

EDIT: Tried formatting as fat16 with a windows XP machine as well, same story.

---

### Post by OoooMatron on 2007-06-24
try another format like fat32 then?

---

