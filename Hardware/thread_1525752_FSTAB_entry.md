---
title: "FSTAB entry"
date: 2010-07-07
forum: Hardware
---

### Post by eaglecoth on 2010-07-07
Hi,

After alot of struggle, I've finally managed to mount some SMB shares belonging to a domain in my system, now, I used the following command:

**sudo mount //server/share /media/myserver/myshare -t smbfs -o credentials=/home/myuser/.smbcredentials -o uid=myuser,gid=mygroup,umask=700,dir_mode=0700,file_mode=0700,rw**

and it works fine,

Now to my question:

What should the corresponding fstab entry look like?  I want to mount this at boot time.

---

### Post by dino99 on 2010-07-07
try mountmanager

---

