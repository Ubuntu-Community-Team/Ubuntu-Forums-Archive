---
title: "Problems with installing UMTSmon on a 64bit machine"
date: 2008-08-09
forum: Hardware
---

### Post by vusko on 2008-08-09
Hello!

Could anyone please help me with this... I'm trying to install the latest version of UMTSmon ([http://sourcforge.net/projects/umtsmon/](http://sourcforge.net/projects/umtsmon/)), I untar it, then **qmake**, but when I type **make clean all**, it throws me a lot of errors, like:

[I].ui/mainwindow.h:12:22:error:qvariant.h: No such file or directory
.ui/mainwindow.h:13:25:error:qmainwindow.h:No such file or directory
.... 
...(and so on like this)...
(and at the end: )
make: *** [obj/main.o] Error 1  [/I]

...and of course, the program could not be compiled. I guess it could be something wrong with qt3? How could I fix this? I would be really thankful for any help.

p.s. I have installed Kubuntu Hardy

---

