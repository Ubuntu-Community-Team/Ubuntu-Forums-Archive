---
title: "gdesklets wont run"
date: 2008-07-30
forum: General Help
---

### Post by nacholand on 2008-07-30
Hi there,
I got a problem with gdesklets.
This is the output that I got when I ran it from the console:

```

Iniciando el servidor gdesklets…
Conectando al servidor [  ###        ]
==========================================================[07/30/08-13:46:05]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]db type could not be determined
in /usr/lib/gdesklets/gdesklets-daemon: line 10 <module>
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
in /usr/lib/gdesklets/main/Starter.py: line 2 <module>
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
in /usr/lib/gdesklets/config/DaemonConfigger.py: line 1 <module>
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
in /usr/lib/gdesklets/config/StateSaver.py: line 128 <module>
in /usr/lib/gdesklets/config/StateSaver.py: line 30 __init__
in /usr/lib/gdesklets/config/Backend.py: line 68 Backend
in /usr/lib/python2.5/shelve.py: line 225 open
in /usr/lib/python2.5/shelve.py: line 209 __init__
in /usr/lib/python2.5/anydbm.py: line 80 open
[EXC]/usr/lib/python2.5/anydbm.py

[---]   75             mod = _defaultmod
[---]   76         else:
[---]   77             raise error, "need 'c' or 'n' flag to open new db"
[---]   78     elif result == "":
[---]   79         # db type cannot be determined
[ERR]>  80         raise error, "db type could not be determined"
[---]   81     else:
[---]   82         mod = __import__(result)
[---]   83     return mod.open(file, flag, mode)


Conectando al servidor [  ###        ]
```

Anyone there had the same problem?
What do you think it could be?

---

