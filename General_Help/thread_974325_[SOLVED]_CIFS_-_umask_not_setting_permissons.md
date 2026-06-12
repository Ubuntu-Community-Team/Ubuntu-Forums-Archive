---
title: "[SOLVED] CIFS - umask not setting permissons"
date: 2008-11-07
forum: General Help
---

### Post by pruhnke on 2008-11-07
Hey all,  I have been searching for some help and didn't find my situation so sorry up front if this has been covered elsewhere, but I can't believe this only happens to me.

I am having a problem with getting a umask to take on a CIFS share with an XP box.

/etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
//192.168.15.2/pictures /mnt/AMD  cifs noexec,credentials=/etc/cifs-AMD,uid=www-data,gid=www-data,umask=022 0 0

```

What is happening here is that my share will then mount with 777 permissions.  So I thought well maybe this is a limitation of CIFS, read only or read write. So I searched and found posts (some admittedly using smbfs instead) where people are discussing umasks in fstab in Ubuntu and it seems to be working like a champ for everyone else.

Here is my pre and post directory permissions for grins using umask=022 or umask=0022.

```

pruhnke@lab:~$ sudo ls -lia /mnt
total 12
819201 drwxr-xr-x  3 root     root     4096 2008-11-07 11:21 .
     2 drwxr-xr-x 21 root     root     4096 2008-10-18 08:26 ..
688265 drwxr-xr-x  2 www-data www-data 4096 2008-11-07 09:11 AMD
pruhnke@lab:~$ sudo mount -v /mnt/AMD
pruhnke@lab:~$ sudo ls -lia /mnt
total 8
819201 drwxr-xr-x  3 root     root     4096 2008-11-07 11:21 .
     2 drwxr-xr-x 21 root     root     4096 2008-10-18 08:26 ..
     2 drwxrwxrwx  1 www-data www-data    0 2008-10-31 14:45 AMD

```

---

### Post by pruhnke on 2008-11-07
I fixed this.

[http://ubuntuforums.org/showthread.php?t=795109&p=4964726](http://ubuntuforums.org/showthread.php?t=795109&p=4964726)

```

pruhnke@lab:~$ grep AMD /etc/fstab
//AMD/pictures /mnt/AMD  cifs ip=192.168.15.2,noexec,credentials=/etc/cifs-AMD,uid=www-data,gid=www-data,file_mode=0755,dir_mode=0755 0 0
pruhnke@lab:~$ sudo mount /mnt/AMD
pruhnke@lab:~$ sudo ls -lia /mnt
total 8
819201 drwxr-xr-x  3 root     root     4096 2008-11-07 11:21 .
     2 drwxr-xr-x 21 root     root     4096 2008-10-18 08:26 ..
     2 drwxr-xr-x  1 www-data www-data    0 2008-10-31 14:45 AMD

```

Hope if anything this helps someone else.

---

### Post by lamachine on 2011-01-09
I'm usign file_mode=0755,dir_mode=0755 and it doesn't work for me all ntfs share is mounted with 777 permissions.  
 I've also posted note here [http://ubuntuforums.org/showthread.php?p=10336886#post10336886](http://ubuntuforums.org/showthread.php?p=10336886#post10336886) . Hope it will ring a bell.  
 Thx for Help.

---

