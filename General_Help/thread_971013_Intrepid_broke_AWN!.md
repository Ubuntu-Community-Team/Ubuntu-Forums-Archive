---
title: "Intrepid broke AWN?!?"
date: 2008-11-04
forum: General Help
---

### Post by Metallinut on 2008-11-04
I had AWN just the way I wanted it.  But when I upgraded to Intrepid, it seems to have broken it.  I wound up doing a complete removal in Synaptic, and reinstalled.  Now it's there on the bottom of my screen, but I cannot run awn-manager to get it back to the way I want.  If I run it in a terminal, I get this:
jp@ubuntu2:~$ awn-
awn-applet-activation  awn-manager            
awn-launcher-editor    awn-schema-to-gconf    
```
jp@ubuntu2:~$ awn-manager 
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 45, in <module>
    from awnTheme import AwnThemeManager
  File "/usr/share/avant-window-navigator/awn-manager/awnTheme.py", line 25, in <module>
    import awn
  File "/usr/lib/python2.5/site-packages/awn/__init__.py", line 31, in <module>
    from awn import *
ImportError: libffi.so.4: cannot open shared object file: No such file or directory
```

Has anyone else seen this?  And if so, do they have a fix?

Thanks,

---

### Post by Kheops_74 on 2008-11-06
Same problem here. No solution for the moment.

K

---

### Post by jeppo on 2008-11-09
Just to confirm, same problem here.

Chris

---

### Post by eternalnewbee on 2008-11-09
It's most probably just a question of reinstalling AWN again.

---

### Post by Kheops_74 on 2008-11-09
Do you know the difference between avant-window-navigator-bzr and avant-window-navigator-bzr package ?

K

---

### Post by eternalnewbee on 2008-11-09
Do you?

---

### Post by Kheops_74 on 2008-11-09
i remove avant-window-navigator-bzr and install avant-window-navigator. It works but i have to configure the applets since some of them are not there anymore like gmail.

K

---

### Post by olejon on 2008-11-09
I think it is better to use the AWN-developers testing packages from their repository. Then you get all the latest applets etc aswell.

You just have to add two software sources and then install 3 packages in Synaptic.

Install howto:

[http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

It will replace other AWN's

---

