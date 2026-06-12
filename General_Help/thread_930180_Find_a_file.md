---
title: "Find a file"
date: 2008-09-25
forum: General Help
---

### Post by dodgingspam on 2008-09-25
I'm trying to setup server and need to find httpd.conf file. How do I find a file on *nux?

---

### Post by spiderbatdad on 2008-09-25
```
locate httpd.conf
```

OR

Places>>Search for Files>> Name contains:httpd.conf; Look in:file system.

---

### Post by sisco311 on 2008-09-25
/etc/httpd/conf/httpd.conf

You can use the find command to find files/folders:
```
find /path/to/dir -type f -name file-name
```
for more info read the man page:
```
man find
``` 
[https://help.ubuntu.com/community/FindingFiles]("https://help.ubuntu.com/community/FindingFiles")

---

### Post by bodhi.zazen on 2008-09-25
You might also want to look at this :

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by dodgingspam on 2008-09-25
great! is there a way to see when the file was last edited?

---

### Post by spiderbatdad on 2008-09-25
:)

---

### Post by bodhi.zazen on 2008-09-25
ls -al

---

### Post by spibou on 2008-09-25
> **dodgingspam said:**
> great! is there a way to see when the file was last edited?
stat file

---

