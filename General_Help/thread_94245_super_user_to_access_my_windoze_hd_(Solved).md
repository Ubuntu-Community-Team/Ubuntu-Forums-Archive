---
title: "super user to access my windoze hd (Solved)"
date: 2005-11-23
forum: General Help
---

### Post by detyabozhye on 2005-11-23
Ubuntu auto detects my windoze hard drive, but I can only access it as super user, and I can't change the permissions to let me read it as a regular user, what should I do?

---

### Post by Specialsauce on 2005-11-23
[QUOTE=detyabozhye]Ubuntu auto detects my windoze hard drive, but I can only access it as super user, and I can't change the permissions to let me read it as a regular user, what should I do?[/QUOTE]
keep using sudo?

---

### Post by detyabozhye on 2005-11-23
Uh, it's kind of tedious to copy files to my home directory using sudo, then change all the user and group on the files and set the permissions. I'd like to be able to browse it as a regular user.

---

### Post by hw-tph on 2005-11-23
Mount it as yourself. Check what your uid and default gid is (refer to /etc/passwd and /etc/group, respectively) and set up /etc/fstab accordingly. The snippet below is from my laptop where the uid is 1000 (first user set up), gid for primary group is also 1000 and using the NTFS filesystem. Obviously you would want a FAT/FAT32 Windows partition for problem free writing.
```
/dev/hda1       /media/hda1     ntfs	user,users,uid=1000,gid=1000	0       0
```
Note that there can be no spaces between the options passed to the mount command, only commas separate the options. For more info, read mount(8) and fstab(5).


H&#229;kan

---

### Post by detyabozhye on 2005-11-23
Thanks. That worked.

---

