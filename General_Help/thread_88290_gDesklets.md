---
title: "gDesklets"
date: 2005-11-09
forum: General Help
---

### Post by wakeboardbum83 on 2005-11-09
Hello All,

I can't seem to get the shell to gDesklets open any more. the daemon comes up and seems to start up fine. but if I try to open the shell I get the following error:

==========================================================[11/09/05-15:37:53]====== Unhandled error! Something bad and unexpected happened.

[EXC]list index out of range
in /usr/lib/gdesklets/gdesklets-shell: line 9 ?
in /usr/lib/gdesklets/shell/PluginRegistry.py: line 52 get_plugin
in /usr/lib/gdesklets/shell/PluginRegistry.py: line 40 get_plugins_by_pattern
in ./Shell/__init__.py: line 70 init
in /usr/lib/gdesklets/shell/Plugin.py: line 18 _get_plugins_by_pattern
in /usr/lib/gdesklets/shell/PluginRegistry.py: line 40 get_plugins_by_pattern
in ./Profiles/__init__.py: line 24 init
in ./Profiles/__init__.py: line 39 __build_menu
in ./Menu/__init__.py: line 169 set_check_item
in ./Menu/__init__.py: line 79 __set_node
[EXC]/usr/lib/gdesklets/shell/plugins/Menu/__init__.py

[---] 74 if (not submenu):
[---] 75 submenu = gtk.Menu()
[---] 76 pitem.set_submenu(submenu)
[---] 77
[---] 78 parent, index = self.__get_node(path)
[ERR]> 79 name, nil, children = parent[index]
[---] 80 parent[index] = (name, item, children)
[---] 81 submenu.insert(item, index)
[---] 82
[---] 83
[---] 84
[---] 85 #
...

if anyone has had this problem and knows how to fix it. any help would be great!!!
Thanks

---

### Post by 23meg on 2005-11-09
Did you by any chance upgrade / uninstall your existing version of python?

---

### Post by wakeboardbum83 on 2005-11-09
No the only thing I did was add a yahoo messenger icon to it and log off. the next time I loged on it was no longer working.

---

### Post by 23meg on 2005-11-09
Do you mean a Yahoo messenger desklet?

---

### Post by wakeboardbum83 on 2005-11-09
No I was adding a shortcut to my starter bar sorry. also my brother told me he did install something using python.

---

### Post by 23meg on 2005-11-09
It looks like a python problem to me. Look into gdesklets' properties in synaptic to find out what version of python it depends on, and make sure it's installed.

---

### Post by wakeboardbum83 on 2005-11-09
I have 2.4 installed...should I try and install 2.0? Thats the version gDesklets has listed... I tried a reinstalled of the 2.4 and that didn't work...

---

### Post by 23meg on 2005-11-10
Where does it list 2.0? To me it seems it needs the most recent version in the Ubuntu repositories, which is 2.4.

---

### Post by wakeboardbum83 on 2005-11-10
When I right click on gdesklets in synaptic in the dependencies lis it has python 2.0 listed in there...

---

### Post by 23meg on 2005-11-10
It shouldn't. Did you install gdesklets from the Breezy repositories? On my system it shows a dependency to the package "python" which is a metapackage that points to the latest python package available, which in turn is 2.4.

---

