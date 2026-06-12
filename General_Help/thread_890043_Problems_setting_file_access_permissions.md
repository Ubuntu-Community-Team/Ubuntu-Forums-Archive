---
title: "Problems setting file access permissions"
date: 2008-08-14
forum: General Help
---

### Post by jgirata on 2008-08-14
Hi,

I'm trying to modify the file access permissions for a file, but my commands are not making any changes.  I'm trying to execute a Java program that is supposed to modify the file (it's a log file), but it's throwing a FileNotFoundException (it says Exception in thread "main" java.io.FileNotFoundException: /path/to/file/server.log (Permission Denied)).  I checked the permissions, and only the owner has write permission.  I tried adding write permission for all files, but when I do

```
sudo chmod a+w server.log
```

nothing happens.  I'm able to remove permissions and add them again, I just can't add write permission for anyone but the owner.  Is there some system setting that is preventing me from doing this?

Thanks in advance!

---

### Post by RealPSL on 2008-08-16
After running ```
sudo chmod a+w server.log
```
provide the output of ```
ls -ld server.log .
```Please include the "." in your command. I want to make sure the permission actually gets changed when you run the command. In addition, in order to modify the file the person modifying the file also needs write access to the directory. It would be preferred to just add them to the correct group instead of giving everyone write access.

---

