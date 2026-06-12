---
title: "chmodding folder and subfolders/files"
date: 2005-12-05
forum: General Help
---

### Post by Irony on 2005-12-05
This command;

*irony@ubuntu:~$ chmod 755 /home/irony/ironclub/newerironclub*

changes the folder newerironclub, but how do I chmod 755 this folder and everything in it to 755 permissions?

---

### Post by dodger on 2005-12-05
chmod -R

(from "man chmod")

---

### Post by Irony on 2005-12-05
Hi thanks for fast respone, just discovered it independently as well;

*irony@ubuntu:~$ chmod -R 755 /home/irony/ironclub*

---

