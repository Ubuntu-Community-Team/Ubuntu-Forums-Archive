---
title: "saving file error."
date: 2008-09-25
forum: General Help
---

### Post by leona on 2008-09-25
Hi there
I have a strange problem.

I have a mounted windows file system.

I can access this mount with no problems.

I can open files, save new files, but I get a problem when trying to save a file that already exists.

If I open a text file, modify it, then try and save it (on the mounted file system) I get an error.  It will just save "Could not save the file" and not tell me why.  If I use the file manager and navigate to the file, delete it, it will then save it, it is very odd.

I've checked permissions, but that all looks fine.

Its an NTFS windows file system I mount if that makes any difference and I mount it with the command.

```

//192.168.1.1/share /home/leona/network cifs username=username,password=pw,uid=leona,gid=leona,file_mode=0777,dir_mode=0777 0 0

```

Any ideas?

Thanks

Leona

---

### Post by russlar on 2008-09-25
hmmm....odd.... are these files marked as read-only on either your linux client or the Windows server?

---

### Post by leona on 2008-09-25
No locks or flags that I can see, I mean I can open the text editor, create a file on that file system, save it, that's fine, make another change and try and save it again, I'll get that error, very very strange :(

---

