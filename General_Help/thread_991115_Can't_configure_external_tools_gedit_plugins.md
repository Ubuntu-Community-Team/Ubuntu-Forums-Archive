---
title: "Can't configure external tools gedit plugins"
date: 2008-11-23
forum: General Help
---

### Post by mvalviar on 2008-11-23
This plug-in is available on my list but I can't configure it. When I click on the configure button nothing happens. When I run gedit on the command line I get:

```
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/externaltools/__init__.py", line 185, in activate
    helper = ExternalToolsWindowHelper(self, window)
  File "/usr/lib/gedit-2/plugins/externaltools/__init__.py", line 121, in __init__
    self._library = ToolLibrary()
  File "/usr/lib/gedit-2/plugins/externaltools/library.py", line 38, in __init__
    os.makedirs(self.locations[0])
  File "/usr/lib/python2.5/os.py", line 171, in makedirs
    mkdir(name, mode)
OSError: [Errno 20] Not a directory: '/home/mvalviar/.gnome2/gedit/tools'
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/externaltools/__init__.py", line 193, in update_ui
    window.get_data(self.WINDOW_DATA_KEY).update_ui()
AttributeError: 'NoneType' object has no attribute 'update_ui'
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/externaltools/__init__.py", line 193, in update_ui
    window.get_data(self.WINDOW_DATA_KEY).update_ui()
AttributeError: 'NoneType' object has no attribute 'update_ui'

```

Please help me. Thanks in advance.

---

### Post by conciseusa on 2009-02-09
I had the same problem, but could find no solution on the net so I tried to solve it myself.

This seems to have worked:
cd ~/.gnome2/gedit/
sudo mkdir tools
sudo chmod 777 tools

It seems there is a bug such that the tools dir is never created. Not sure if the 777 tools is a bad idea, but I could not save a new tool with out it.

---

