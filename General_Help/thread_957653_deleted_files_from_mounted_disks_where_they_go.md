---
title: "deleted files from mounted disks where they go???"
date: 2008-10-24
forum: General Help
---

### Post by ra2008 on 2008-10-24
hi,,,

when i delete files from a mounted disk (partition) they dont appear in the waste basket?
where they go?
thanks

---

### Post by TeoBigusGeekus on 2008-10-24
Check the
```
/pathtomounteddisk/.Trash-1000
```
folder

---

### Post by bab1 on 2008-10-24
If you deleted them from the command line ie:```
rm -f <somefile>
``` They're gone.

If you deleted them using Nautilus from```
/media/<some_dir>
``` then they should be in a hidden file at <some_dir>.  I believe it is .Trash.  Use cntl-h to confirm this.

If you deleted them using Nautilus from the other partitions you may have, the deleted files should be in your home directory .Trash ```
~/.Trash
```

---

### Post by ra2008 on 2008-10-25
hi ,
non of the above worked..
???

---

### Post by bab1 on 2008-10-25
> **ra2008 said:**
> hi ,
non of the above worked..
???

What didn't work?

Explain what you are doing in more detail.  What is the mount point for The:> files from a mounted disk (partition)

What commmand or GUI action are you using to delete the files?

---

### Post by ra2008 on 2008-10-25
hi,
my PC used to run WinXp. after i installed Ubuntu i dual boot. the old WinXp partitions are mounted to /media/driveD 
I delete files either by right click --> delete or press delete button from keyboard.

---

### Post by bab1 on 2008-10-25
Don'tt know what to say.  I have mounted a partition at /media and it works as I said.> If you deleted them using Nautilus from
Code:

/media/<some_dir>

then they should be in a hidden file at <some_dir>. I believe it is .Trash. Use cntl-h to confirm this.


Actually it is .Trash-<username>

---

### Post by ra2008 on 2008-10-28
> **bab1 said:**
> 
Actually it is .Trash-<username>

if .Trash-<username> is in the same drive i.e. /meda/mydrive, then i couldnt find it yet,,,
does the drive format matters?
it is ntfs.

thanks

---

### Post by alienprdkt on 2008-10-28
try 
#sudo bash
#gksudo nautilus

which will open nautilus with root permissions, then go to your /media<mounted-partition> and view hidden folders
look for trash can

---

### Post by ra2008 on 2008-10-30
> **alienprdkt said:**
> try 
#sudo bash
#gksudo nautilus

which will open nautilus with root permissions, then go to your /media<mounted-partition> and view hidden folders
look for trash can

when i search a filename in the search bar above, i cant get the hidden files, although they exist.
???

---

