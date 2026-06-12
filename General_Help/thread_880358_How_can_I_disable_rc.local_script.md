---
title: "How can I disable rc.local script?"
date: 2008-08-04
forum: General Help
---

### Post by coqui1212 on 2008-08-04
Well I made it executable to let it start my wireless configuration at boot but now I have no need for it. It says in order to disable it I just have to change the execution bits. I don't understand this since I am a recent windows convert

---

### Post by x1a4 on 2008-08-04
```
sudo chmod -x /etc/rc.local
```

---

### Post by coqui1212 on 2008-08-05
Well how can I now make sure it is disabled I am pretty sure there is a way right? Thank you for being helpful

---

### Post by Krupski on 2008-08-05
> **coqui1212 said:**
> Well how can I now make sure it is disabled I am pretty sure there is a way right? Thank you for being helpful

Normally, rc.local doesn't DO anything. It only contains "exit 0" if you didn't edit it.

To disable it, you can remove the executable permissions (i.e. sudo chmod 0644 /etc/rc.local to disable it and sudo chmod 0755 /etc/rc.local to enable it), or you can edit the file and place comment marks (#) after every line... or rename it.

If you rename it though... your machine might not boot if it can't fine 'rc.local'. I don't know for sure... never tried it.

---

### Post by x1a4 on 2008-08-05
> **coqui1212 said:**
> Well how can I now make sure it is disabled I am pretty sure there is a way right? Thank you for being helpful

Once the execute bit is removed the file is no longer an executable and will not execute, i.e.: it is disabled. You can verify like so:
```
ls -l /etc/rc.local
```
If there is no **x** anywhere in the persmissions column (first column) it's not an executable. On mine it's:
```
**-rwxr-xr-x** 1 root root 489 2008-06-27 13:19 /etc/rc.local*
```
This means that the file can be read and executed by all, and written to by its owner, in this case root.

---

