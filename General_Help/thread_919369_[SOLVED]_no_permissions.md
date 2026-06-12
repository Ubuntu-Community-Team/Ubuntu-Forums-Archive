---
title: "[SOLVED] no permissions"
date: 2008-09-13
forum: General Help
---

### Post by rossjman1 on 2008-09-13
I just downloaded America's Army for Linux, and I can't run the installer.
```

jeff@jeff-laptop:~/Desktop$ ./armyops250linux.run
bash: ./armyops250linux.run: Permission denied
jeff@jeff-laptop:~/Desktop$ sudo su
root@jeff-laptop:/home/jeff/Desktop# ./armyops250linux.run
bash: ./armyops250linux.run: Permission denied
root@jeff-laptop:/home/jeff/Desktop#

jeff@jeff-laptop:~/Desktop$ ls -l
total 797840
-rw-rw---- 1 jeff jeff 813453963 2008-09-13 21:56 armyops250linux.run

```

Nevermind, chmod +x filename did it

---

### Post by Pro-reason on 2008-09-13
Installers generally need to be run as [root]("https://help.ubuntu.com/community/RootSudo").

```

sudo ./armyops250linux.run

```

---

### Post by sisco311 on 2008-09-13
make it executable:
```
chmod +x ./armyops250linux.run
```

---

