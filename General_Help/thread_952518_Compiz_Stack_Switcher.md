---
title: "Compiz Stack Switcher"
date: 2008-10-19
forum: General Help
---

### Post by tom66 on 2008-10-19
I tried the following commands as recommended on the Compiz forums in an attempt to get Stack Switcher, but it does not work.

```

thomas@titanic:~$ git-clone git://anongit.compiz-fusion.org/fusion/plugins/stackswitch
Initialized empty Git repository in /home/thomas/stackswitch/.git/
remote: Counting objects: 20, done.
remote: Compressing objects: 100% (18/18), done.
remote: Total 20 (delta 7), reused 0 (delta 0)
Receiving objects: 100% (20/20), 16.03 KiB, done.
Resolving deltas: 100% (7/7), done.
thomas@titanic:~$ cd stackswitch
thomas@titanic:~/stackswitch$ make && make install
Makefile:58: *** [ERROR] Package pangocairo was not found in the pkg-config search path. Perhaps you should add the directory containing `pangocairo.pc' to the PKG_CONFIG_PATH environment variable Package 'pangocairo', required by 'compiz-text', not found. Stop.
thomas@titanic:~/stackswitch$  

```

If anyone could help, that would be great.

---

### Post by okiniko on 2008-12-24
Install the pango-devel package, that should give you the file you need.

---

