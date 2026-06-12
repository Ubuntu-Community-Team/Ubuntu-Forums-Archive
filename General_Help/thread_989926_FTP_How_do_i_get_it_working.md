---
title: "FTP: How do i get it working??"
date: 2008-11-22
forum: General Help
---

### Post by Monotoko on 2008-11-22
Hiya, i followed the instructions to get proftpd and gproftpd to set up an FTP server, these worked before now, but i have just upgraded to 8.10.

After installing them though, when i try to run gproftpd i get

```
Failed to execute child process "su-to-root" (No such file or directory)
```

what does that mean??:confused:

---

### Post by marshall.robert on 2008-11-22
have you tried reinstalling the app? i have found that every upgrade has gone wrong in some way...

---

### Post by deadowl on 2008-11-22
I would recommend using sftp (you can set that up by installing openssh-server).

---

### Post by grazzt_85 on 2008-11-22
I use vsftpd and it works perfectly! When you install it, an ftp root directory is created at the home folder that can be anonymously accessed right away, you only have to edit the permissions on that folder to your liking. It has a conf file if you want extra features (user creation, passwords, encryption) but it is very understandable since there are descriptions of everything in it.

---

### Post by Monotoko on 2008-11-22
using vsftpd as suggested in the post above, i get:
```
500 OOPS: could not bind listening IPv4 socket
```

---

