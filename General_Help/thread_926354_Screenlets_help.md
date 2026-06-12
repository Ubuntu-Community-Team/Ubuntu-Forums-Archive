---
title: "Screenlets help"
date: 2008-09-21
forum: General Help
---

### Post by vlad_1394 on 2008-09-21
Whenever I try to install screenlets this is what I get. Can anyone help me out????:mad:


vlad@vlad-laptop:~$ sudo apt-get install screenlets

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by anotherdisciple on 2008-09-23
Open a terminal and type this:

```
sudo dpkg --configure -a
```

Simple eh? A lot of people have this problem. It happens when you are installing or updating and something forces it to quit prematurely.

---

