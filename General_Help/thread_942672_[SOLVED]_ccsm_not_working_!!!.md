---
title: "[SOLVED] ccsm not working !!!"
date: 2008-10-09
forum: General Help
---

### Post by celticbhoy on 2008-10-09
For some reason I cant get ccsm to work, when I run it in a terminal I get :-

gary@Ubuntu-0:~$ ccsm
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 99, in <module>
    import compizconfig
ImportError: /usr/local/lib/python2.5/site-packages/compizconfig.so: undefined symbol: ccsGetPluginStrExtensions

Any ideas. OBTW apart from that compiz is working fine.

---

### Post by celticbhoy on 2008-10-09
Managed to fix it with some re-installing.

---

### Post by vcuauhtemoc on 2008-10-13
Hey, I've got the same problem. What exactly did you reinstall?

---

### Post by celticbhoy on 2008-10-14
basically i un-installed everything to do with compiz from synaptic with complete removal then installed them all again. My config was untouched so my settings stayed the same.

---

### Post by celticbhoy on 2008-10-14
BTW are you using GIT?

---

