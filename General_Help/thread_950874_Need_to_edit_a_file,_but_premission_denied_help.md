---
title: "Need to edit a file, but premission denied help"
date: 2008-10-17
forum: General Help
---

### Post by gevo12321 on 2008-10-17
ok so im completely new to ubuntu, and am trying to get my computer to work properly, and the audio out jack doesnt work in ubuntu(it works in vista). so i researched it and found that i need to add a certain line to a file in the ect folder, however everytime i try to save the edited file, it says premission denied. can someone please help me?

---

### Post by zvacet on 2008-10-17
In terminal type

```
gksudo gedit /etc/filename
```

**filename** is name of your file

---

### Post by jocko on 2008-10-17
> **gevo12321 said:**
> ok so im completely new to ubuntu, and am trying to get my computer to work properly, and the audio out jack doesnt work in ubuntu(it works in vista). so i researched it and found that i need to add a certain line to a file in the ect folder, however everytime i try to save the edited file, it says premission denied. can someone please help me?

You need to have root permissions to be able to edit files outside your home directory.
To edit the file as root type this in a terminal:
```
gksudo gedit /etc/[COLOR=Red]FILENAME[/COLOR]
``` Change FILENAME to whatever the file is named.

---

### Post by bodhi.zazen on 2008-10-17
See also :

[uhelp]community/FilePermissions[/uhelp]

[uwiki]RootSudo[/uwiki]

---

