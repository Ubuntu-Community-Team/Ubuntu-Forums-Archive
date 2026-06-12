---
title: "AWN won't launch"
date: 2008-09-28
forum: General Help
---

### Post by dbbolton on 2008-09-28
I installed AWN from this repository:

[https://launchpad.net/~awn-testing/+archive](https://launchpad.net/~awn-testing/+archive)

When I try to launch avant-window-navigator I get this message:

```

avant-window-navigator: error while loading shared libraries: libwnck-1.so.18: cannot open shared object file: No such file or directory

```

Any thoughts?

---

### Post by dbbolton on 2008-09-28
Edit: I remember that I had compiled AWN from source awhile ago, so I ran "make uninstall" from the proper directory. Then, I re-installed the packages from the launchpad repo. Now when I launch avant-window navigator, I get this message:

```

bash: /usr/local/bin/avant-window-navigator: No such file or directory

```

When I try to launch /usr/bin/avant-window-navigator I get:

```

Traceback (most recent call last):
  File "/usr/share/avant-window-navigator/awn-applets-migration.py", line 3, in <module>
    import awn
  File "/usr/local/lib/python2.5/site-packages/awn/__init__.py", line 13, in <module>
    from awn import *
ImportError: /usr/local/lib/python2.5/site-packages/awn/awn.so: undefined symbol: awn_effect_start_ex

```

---

### Post by jobo1313 on 2008-09-28
Do you have effects off. If you do you will need to turn them on.

---

