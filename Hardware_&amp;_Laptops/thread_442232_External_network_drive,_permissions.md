---
title: "External network drive, permissions"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by r33z on 2007-05-13
Hi I'm new to Linux and having problem with permissions on my mounted networkdrives. I have a maxtor share storage drive and when mounting it I only have permission to create a file or folder, afterwards I can't write in the new folder or change the files. By some reason the new file is owned by user 35000

```
user@user-laptop:~$ ls -l /media/maxtor_Privat/
total 59392
drwxr-xr-x 4 35000 root        0 2007-04-19 22:28 Bilder
.

```

my fstab
```
//maxtorsafe/Privat /media/maxtor_Privat cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```

anyone that can see what I have done wrong?

---

### Post by depele on 2007-05-23
I am terribly sorry, 
I can't find the answer myself.

grtz...
somebody else?

---

### Post by d3v1us on 2007-06-06
i've been having this problem too.  i have a maxtor 300 gig that i can't store to. :(

---

