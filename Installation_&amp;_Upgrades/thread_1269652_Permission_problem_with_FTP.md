---
title: "Permission problem with FTP"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by aangel on 2009-09-18
Hi, I'm setting up FTP on 8.04 and am having trouble with permissions.
Using either vsftp or sftp, I can't cd into or list the contents of a directory used to hold a website.

The folder permissions are:
```
drwxrw-rw- 15 www-data www-data 4096 2009-09-15 14:17 davinci
```

Here are the relevant users:
```
us-adminpg:x:1000:33:us-adminpg,,,:/home/us-adminpg:/bin/bash
www-data:x:33:33:www-data:/var/www:/bin/sh

```

Groups for us-adminpg:
```
us-adminpg@sf-davinci:/var/www$ id
uid=1000(us-adminpg) gid=1000(us-adminpg) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),109(lpadmin),115(admin),124(sambashare),1000(us-adminpg)
```

Steps:
1. Log in at us-adminpg.
2. cd /var/www/davinci
3. Receive "Can't change directory"

I thought I understood Linux permissions, it seems that I don't. Does anyone see what's missing?

---

### Post by imhotep59 on 2009-09-18
Your directory www-data should have access permission for groups and users. So it should look like that : drwxrwxrwx

For a directory 'x' means that you have access to its contents (for a file 'x' means that you can execute this file, i.e a script)

(Hope i was clear)

---

### Post by aangel on 2009-09-18
Thank you! That was exactly what I was missing. I was trying to be parsimonious with permissions and had forgotten the role of x.

---

