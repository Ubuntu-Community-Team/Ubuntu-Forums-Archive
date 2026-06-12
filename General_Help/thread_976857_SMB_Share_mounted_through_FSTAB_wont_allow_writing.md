---
title: "SMB Share mounted through FSTAB wont allow writing permissions"
date: 2008-11-09
forum: General Help
---

### Post by ChRziz on 2008-11-09
I'm having problems with mounting samba shares from other computers. Here is my fstab: [http://paste.ubuntu.com/69789/](http://paste.ubuntu.com/69789/) - The one with the .65 ip works perfect, yet the other mounts, but it wont let me have write permissions. It gives me a "Permission Denied error."

I attempted to just chmod it yet that didnt work either.

Both computers samba shares are configured the same with the same permissions. Only differences is the .45 maching is running XP and .65 vista.

I can read write if I access either of them through nautilus using "smb://192.168.1.65 ...." yet I want them to automount read/write permissions through the fstab file.

Any information would be appreciated. Thank you!

Update: It shows a lock icon on the folder it wont let me write to. Just wanted to mention that if it might help to better diagnose the problem.

---

### Post by ChRziz on 2008-11-09
I tried the following commands to change the owner. Here's what I get

root@chrziz-toshiba:/home/chrziz# chown chrziz /mnt/Files
chown: changing ownership of `/mnt/Files': Permission denied
root@chrziz-toshiba:/home/chrziz# 

Doesn't root have the permissions to do anything?

The only way I can add files to that share is run Nautilus as root. I even tried changing the permissions through nautilus and they reset themself.

This makes no sense.

---

### Post by Iowan on 2008-11-09
Try it with **cifs**:
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

---

### Post by ChRziz on 2008-11-10
Thanks! I will try it out.

---

