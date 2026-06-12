---
title: "I feel a little stupid asking this. File administration question."
date: 2008-11-27
forum: General Help
---

### Post by Mamsaac on 2008-11-27
So, I set up a SSH server... but thing is that a user that has no rights to write a file can still delete it. How does that work? Thanks in advance for the answer.

---

### Post by unutbu on 2008-11-27
Yes, I was surprised by this recently too.
It turns out that if you have write permission on the parent directory, then you can delete any file in that directory.

For example, 

```
stop@intersection:~/test% cd
stop@intersection:~% sudo touch ICanDeleteRootOwnedFile
[sudo] password for stop:
stop@intersection:~% ls -l ICanDeleteRootOwnedFile 
-rw-r--r-- 1 root root 0 2008-11-27 21:55 ICanDeleteRootOwnedFile
stop@intersection:~% rm ICanDeleteRootOwnedFile 
rm: remove write-protected regular empty file `ICanDeleteRootOwnedFile'? y
stop@intersection:~% ls -l ICanDeleteRootOwnedFile 
ls: ICanDeleteRootOwnedFile: No such file or directory
```

I can delete root's file because it is in /home/stop.

For all the details, see [http://www.albany.edu/faculty/gms/homepage101/unix_permissions.html#directory](http://www.albany.edu/faculty/gms/homepage101/unix_permissions.html#directory)

---

### Post by Mamsaac on 2008-11-27
Oh, I just changed the user group and it's fixed. Thanks.

---

### Post by unutbu on 2008-11-27
Yes, you can definitely prevent that using permissions.

If you run
```

chmod -R go-w /home/mamsaac
```
then nobody but root and mamsaac can delete anything in /home/mamsaac.

If you don't want anyone other than mamsaac (and root) from having the ability to read or write any future file you create, then add
```

umask 077
```

to your ~/.bashrc.

---

### Post by Mamsaac on 2008-11-28
Thanks for such a straight and clear answer =)

---

