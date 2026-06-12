---
title: "gksudo nautilus returns error message."
date: 2008-09-02
forum: General Help
---

### Post by pravin03 on 2008-09-02
praveen@praveen-desktop:~$ gksudo nautilus
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:7959): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> trash:///

(nautilus:7959): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:7959): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown
praveen@praveen-desktop:~$ 





what is the problem?

---

### Post by Luke771 on 2008-09-02
try doing gksu nautilus instead of gksudo

---

### Post by pravin03 on 2008-09-02
praveen@praveen-desktop:~$ gksu nautilus
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:6906): WARNING **: Unable to add monitor: Operation not supported

---

### Post by rfourie on 2008-10-05
i installed samba (not just samba-common) and it that solved it.

---

