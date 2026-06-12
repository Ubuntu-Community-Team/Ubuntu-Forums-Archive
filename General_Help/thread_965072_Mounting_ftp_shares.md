---
title: "Mounting ftp shares"
date: 2008-10-31
forum: General Help
---

### Post by ezramorris on 2008-10-31
Hi,
I'm trying to mount an FTP share in my home directory. It should only be mountable and accessible by me.

So far I've put
```
curlftpfs#user:pass@server /home/user/dir fuse defaults,uid=1000,gid=1000,umask=007 0 0
```
into /etc/fstab, but only root can mount and access it.

Even if I try to cd into it, I get "Permission denied".

Any ideas?
Thanks.

---

### Post by ezramorris on 2008-11-02
anyone?

---

### Post by krisik28 on 2009-03-23
Maybe try to add somewhere :
```
 allow_other 
```
regards krisik28

---

### Post by ezramorris on 2009-03-24
Thanks, I sorted it.

---

