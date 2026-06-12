---
title: "&quot;Hardware Drivers&quot; won't open"
date: 2008-07-28
forum: General Help
---

### Post by evanct on 2008-07-28
It usually asks me for my password, I enter it, and nothing happens. here is the output:

```
evan@evans-computer:~$ gksu -D /usr/share/applications/jockey-gtk.desktop /usr/bin/jockey-gtk
File "/usr/bin/jockey-gtk", line 300, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.5/site-packages/jockey/ui.py", line 269, in run
    self.ui_init()
  File "/usr/bin/jockey-gtk", line 93, in ui_init
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 240, in update_tree_model
    is_enabled = handler.enabled()
  File "/usr/share/jockey/handlers/nvidia.py", line 51, in enabled
    devices = self.xorg_conf.getSections('device') 
AttributeError: 'NoneType' object has no attribute 'getSections'
```

can anyone help?

---

### Post by evanct on 2008-07-28
bump?

---

