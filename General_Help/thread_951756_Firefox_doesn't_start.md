---
title: "Firefox doesn't start"
date: 2008-10-18
forum: General Help
---

### Post by dplecto on 2008-10-18
firefox fails to start - I tried to run it from commandline and this is what I get:

```
:~$ firefox
Killed
```


Then, I ran a strace:

```
:~$ strace firefox
execve("/usr/bin/firefox", ["firefox"], [/* 35 vars */]) = -1 EACCES (Permission denied)
+++ killed by SIGKILL +++
Process 30607 detached
```

Ok. So, this has got something to do with misplaced permissions - no I attempted to run firefox as root and in safe mode: 
This is what i get:

```
sudo strace firefox -safe-mode
execve("/usr/bin/firefox", ["firefox", "-safe-mode"], [/* 16 vars */]) = -1 EACCES (Permission denied)
+++ killed by SIGKILL +++
Process 30980 detached
```

Does anyone know which file does [/* 32 vars */] refers to ?

All this started to happen after I performed a routine daily update and then a restart. 

More interestingly, this happens only with the firefox installed from synaptic - I compiled and installed firefox from source and there wasn't any problems. (I didn't install it to standard path - instead to /opt/sfw/firefox & added firefox to the global path) I would have stuck to that method if it were not for the fact that then, I would have to manually fix up all the file handlers/ pluggins in firefox (e.g i couldn't play divx videos online because the totem movie plugin wasn't installed or something like that). 

Can someone help me with fixing firefox up please ?

Thanks,

d

---

