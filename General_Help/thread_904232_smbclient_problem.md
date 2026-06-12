---
title: "smbclient problem"
date: 2008-08-29
forum: General Help
---

### Post by j.bunce on 2008-08-29
Hi, 

I've got an error with smbclient that I can't seem to solve. This is the error I am seeing:

user@hostname:~$ smbclient \\\\192.168.120.1\\fileshare
Unknown parameter encountered: "_SNDBUF"
Ignoring unknown parameter "_SNDBUF"
params.c:Parameter() - Ignoring badly formed line in configuration file: :
Unknown socket option SO

However an identical set up is on a different subnet has no error. I've double checked and this is not network error.

Any ideas?

---

### Post by j.bunce on 2008-08-29
Found out why, in /etc/samba/smb.conf  SO_SNDBUF=8192 was spread over two lines...no idea how that happened!

:)

---

### Post by Nepherte on 2008-08-29
This might save you some '\'s:
```
smbclient //192.168.120.1/fileshare
```

---

