---
title: "[SOLVED] Where is glipper"
date: 2008-09-01
forum: General Help
---

### Post by enderal on 2008-09-01
I have downloaded and installed, removed and reinstalled glipper but where is it? I know where it is in the files at /usr/lib/glipper. 

When I run in terminal I get...
SHARED_DATA_DIR: /usr/share/glipper
Binding shortcut <Ctrl><Alt>c to popup glipper
Running with options: {'standalone': False}

<Ctrl><Alt>c doesn't do anything. Neither does clicking run.

 I had it running once awhile back. Is there a certain way to load it? I really need a clipboard manager.

Thanks.

---

### Post by Catalyst2Death on 2008-09-01
You may need to remove the old glipper config:

```
$ rm -r ~/.glipper
```

source:
[http://glipper.sourceforge.net/](http://glipper.sourceforge.net/)

---

### Post by enderal on 2008-09-01
Nope. Uninstalled Removed config. Reinstalled. Still the same.

---

### Post by oldos2er on 2008-09-01
The new Glipper installs as a panel applet. Right-click somewhere on your panel, choose add applet, then clipboard manager (I think that's the name for it).

---

### Post by enderal on 2008-09-01
It seems to be working now.

Thank you.

---

