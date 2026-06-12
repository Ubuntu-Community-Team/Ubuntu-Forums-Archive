---
title: "Mount ext3 writable?"
date: 2005-02-27
forum: Hardware &amp; Laptops
---

### Post by Shambler on 2005-02-27
I have an ext3 partition which I want to mount so that every user can write on it. I did insert this into /etc/fstab:
```
/dev/sda1 /mnt/data1 ext3 user,rw 0 0
```
but no user can write on it...

---

### Post by alastair on 2005-02-27
It is not just a question of mounting "rw" - but unix permissions as well.

The user needs write permission to the file or directory - either via permissions, or ownership (user/group).
Who owns the directory on /mnt/data1 where you are trying to write? And what are the perms?

---

### Post by Shambler on 2005-02-27
It is rwxr-xr-x root root

---

### Post by bored2k on 2005-02-27
[QUOTE=Shambler]It is rwxr-xr-x root root[/QUOTE]
/dev/hda1       /mnt/data1    ext3    umask=000       0       0

---

### Post by Shambler on 2005-02-27
Hm, this is what "dmesg | tail" says:
```
EXT3-fs: Unrecognized mount option "umask=000" or missing value
```
I think this option only works for fat...

---

### Post by alastair on 2005-02-27
[QUOTE=Shambler]Hm, this is what "dmesg | tail" says:
```
EXT3-fs: Unrecognized mount option "umask=000" or missing value
```
I think this option only works for fat...[/QUOTE]
 If a directory has permissions :

rwxr-xr-x  root root

then this is writable by user root only. Try using :

sudo echo "hello" > /mnt/data1/hello

You don't need "umask" mount options - just mount the directory e.g.

mount /dev/hda1 /mnt/data1

Then :

chmod 777 /mnt/data1
or
chown <yourlogin>.<yourgroup> /mnt/data1

---

### Post by Shambler on 2005-02-28
Yeah, the funny thing is that you have to chmod after the mount, not before... Then it works...

---

### Post by doitashimashite on 2005-02-28
Try the /etc/fstab entry:

/dev/sda1 /mnt/data1 ext3 defaults 0 0

---

### Post by kafton on 2005-02-28
I believe that the default action in fstab is to mount the partitions at system startup unless you specify otherwise. The only user the system knows is root at that time. You could put  

/dev/sda1 /mnt/data1 ext3 user,noauto,rw 0 0

in fstab and then it would have to be mounted with

mount /mnt/data1    --no sudo--

by each user.

---

