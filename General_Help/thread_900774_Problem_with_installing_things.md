---
title: "Problem with installing things"
date: 2008-08-25
forum: General Help
---

### Post by Rickyk on 2008-08-25
When i got to install or uninstall i get this message

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


```
I tryed to do this and i get this

```
ricky@Ricky:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
ricky@Ricky:~$ 

```

What do i do?

---

### Post by tuxxy on 2008-08-25
Enter a **sudo** to the start of the command to assign it admin privs

```
sudo dpkg --configure -a
```

---

### Post by sisco311 on 2008-08-25
run the command as root:
```
sudo dpkg --configure -a
```

---

