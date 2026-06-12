---
title: "[SOLVED] Simple Terminal Window Help"
date: 2008-09-25
forum: General Help
---

### Post by AmbiguousOutlier on 2008-09-25
I'm trying to get to my desktop then run sudo dpkg -i ndis*, I've downloaded the relevant files and i can see them on my desktop.

can someone see what i'm doing wrong?

```

rhys@Orange:~$ cd ~/desktop
bash: cd: /home/rhys/desktop: No such file or directory
rhys@Orange:~$ cd desktop
bash: cd: desktop: No such file or directory
rhys@Orange:~$ cd /desktop
bash: cd: /desktop: No such file or directory
rhys@Orange:~$ sudo dpkg -i ndis*
[sudo] password for rhys: 
dpkg: error processing ndis* (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndis*
rhys@Orange:~$ 

```

---

### Post by AmbiguousOutlier on 2008-09-25
Solved it I need a Captial D for desktop.

Thanks me.

EDIT:
I can't find the link that says this thread is solved.

---

