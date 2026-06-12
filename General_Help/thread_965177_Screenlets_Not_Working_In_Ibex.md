---
title: "Screenlets Not Working In Ibex"
date: 2008-10-31
forum: General Help
---

### Post by joey-elijah on 2008-10-31
Hey all, my screenlets have gone!

They worked/started up fine in the ibex beta and RC, but since a debian core update they no longer start up with my machine.

If i try and launch the screenlets manager all i get is the spinning cursor wheel for a few secs and then nada. Nothing.

Trying to launch via terminal gives me: -

```
ile "/usr/share/screenlets-manager/screenlets-manager.py", line 25, in <module>
    import pygtk
ImportError: No module named pygtk

```However, i downloaded the Tar.gz but it won't install. 

is there some obvious explanation/fix?

EDIT: -- Emesene won't start either. This is duh a python issue. How can i fix/correct this?

---

### Post by joey-elijah on 2008-10-31
trying to run emesene gives me 

> Traceback (most recent call last):
  File "/usr/share/emesene/Controller.py", line 21, in <module>
    import gtk
ImportError: No module named gtk


---

### Post by mastergreg on 2008-12-10
Same issue here everything that uses pyhton and pygtk crashed
i wonder if the dev packages would help
no connection on my ibex pls try and let me know
emesene glchess screenlets all down.

---

### Post by mastergreg on 2008-12-10
Same issue here everything that uses pyhton and pygtk crashed
i wonder if the dev packages would help
no connection on my ibex pls try and let me know
emesene glchess screenlets all down.

---

