---
title: "Saving output to log a file"
date: 2005-11-26
forum: General Help
---

### Post by Roman27 on 2005-11-26
How come this isn't working?

```
dim8300:~$ sudo echo ===================== >>/var/log/cat.log
bash: /var/log/cat.log: Permission denied
```

I have "touched" the file, so it does exist.  It is owned by root and has perms of 644

---

### Post by Roman27 on 2005-11-26
Hmmm...  Nevermind...  It works fine in a root terminal, but not through sudo.  Strange...

---

### Post by hw-tph on 2005-11-26
I have come across similar problems before. My quick and ugly solution was saving the output to temporary file and **sudo cp -f tmpfile targetfile**. It appears sudo doesn't work across pipes but I haven't investigated the problem any more than that.


Håkan

---

