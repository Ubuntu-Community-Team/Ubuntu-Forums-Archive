---
title: "NAS: Error splicing file"
date: 2020-09-01
forum: Hardware
---

### Post by yetanotheruser on 2020-09-01
Hi everyone! 
I'm getting this error message while copying files from my Samba/Cifs NAS to my drive. I'm running Ubuntu 20.04 using Nemo 4.4.2

```
Error while copying 'filename'
There was an error copying the file into '/destination'
Error splicing file: Input/output error
```

cp also yields an error

```
cp /media/NAS\ Storage/file .
cp: error reading '/media/NAS Storage/file': Input/output error
```

More info & more weirdness:
- Another machine with Ubuntu & Nautilus has the same problem
- But my Windows machine does not
- Files are partially copied but miss the last few MBs.
- Opening files from my NAS in the appropriate program works fine.
- FTP and rsync work fine
- This is my fstab
```
# Nas Storage "Volume_1" on 192.168.1.140
//192.168.1.140/Volume_1    /media/NAS\040Storage        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777,vers=1.0 0 0

```
Note: the second machine has no blank spaces in the mount point, and it still doesn't work
- I can upload files to the NAS, copy from NAS to itself fine
- Small files almost always work, large ones rarely (>500MB)

---

### Post by CelticWarrior on 2020-09-01
Which file system do you have in the location you're copying the files **to**&#8203;?

---

### Post by yetanotheruser on 2020-09-01
> **CelticWarrior said:**
> Which file system do you have in the location you're copying the files **to**&#8203;?

Thanks for the reply!
My Ubuntu computers are ext4 and I tried an USB drive which I think is Fat32 (none work)

Edit: also tried copying to a NTFS hard drive, it failed at about 40%
:(

---

### Post by CelticWarrior on 2020-09-01
```
[COLOR=#000000][FONT=&quot]Error splicing file: Input/output error[/FONT][/COLOR]
```

[COLOR=#000000][FONT=&quot]I've asked because this ^^^ suggests the target is FAT32 or something, i.e., a file system that has a short limit for files size. If you try to copy a file with more than 4GB (I think) to a FAT32 partition you'll get that exact error.
[/FONT][/COLOR]

---

### Post by yetanotheruser on 2020-09-01
> **CelticWarrior said:**
> ```
[COLOR=#000000][FONT=&quot]Error splicing file: Input/output error[/FONT][/COLOR]
```

[COLOR=#000000][FONT=&quot]I've asked because this ^^^ suggests the target is FAT32 or something, i.e., a file system that has a short limit for files size. If you try to copy a file with more than 4GB (I think) to a FAT32 partition you'll get that exact error.
[/FONT][/COLOR]
Unfortunately it seems the parameters are not those, ie. trasfers fail for ~500MB files and lower and many types of filesystem

---

