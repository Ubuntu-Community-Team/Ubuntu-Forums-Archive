---
title: "Error opening file 'media/drive/filename.*': No space left on device"
date: 2008-11-21
forum: General Help
---

### Post by jimsheep on 2008-11-21
I have researched this issue and have not found any information whatever on it.  I am attempting to copy to a 1GB CarMP3-brand car MP3 player. I've a few files on there now, and the free space is reported as 221.5MB.

I try to copy anything to the drive and it gives me the following error:

```
Error opening file '/media/drive/file.*': No space left on device
```

when i run df -h in /usr/local/src, the drive appears as follows:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdd              992M  771M  222M  78% /media/MY AUDIO
```

I try to create an empty file, same error.  I have un-mounted and re-mounted the drive, unplugged and re-plugged both connections, et cetera, and still have the same results.

Do I need to format the drive?  There are no hidden folders, even when i look with gksudo nautilus.

---

### Post by __Ryan__ on 2008-11-22
Is the device mount read-only? 

Try...

```
ls -l /media/MY\ AUDIO
```

---

### Post by jimsheep on 2008-11-22
I get a list of the files that are on the drive, and they all have '-rwx------' before them.

if i remove a file, i can replace that file.  it's almost like the drive is misreporting either its size or the file sizes.

---

