---
title: "app - Where is it"
date: 2008-11-12
forum: General Help
---

### Post by Quarkrad on 2008-11-12
To sort out a problem I have been told:

Go to Applications --> System Tools --> Configuration Editor

but under Applications I have no System Tools option.  If I launch Add/Remove and search on Configuration Editor it has a tick against it - I understand this means this app is installed.  But where is it and how do I launch it?  Sorry to ask a dumb question but how many applications are installed that could be of use but I do not know where they are?

---

### Post by fooman on 2008-11-12
to launch it....you could open a terminal and type:

```
gconf-editor
```

then hit enter.

or press alt-f2 and type the same into that box...then press run.

---

### Post by Wayne_V on 2008-11-12
Can you tell us what version you are running (e.g. 8.10 Ubuntu)?

Can you right click on Applications and select Edit Menus.

You could also go to 'Applications->Add/Remove'  and set show to 'installed applications only' to review what is installed.

---

### Post by issih on 2008-11-12
Hmmn, its probably just a matter of editing your main menu to get the shortcut (right click on the menu and select to edit it)

Alternatively open a terminal (or the run application dialog alt+f2) and run gconf-editor

Hope that helps

---

### Post by mick222 on 2008-11-12
Can you say what you  need it for.

---

### Post by Quarkrad on 2008-11-12
Thank you all - in the end I right clicked the Ubuntu icon top left of screen and chose Edit Menus.  Clicked System Tool - and then checked the configuration editor box.

---

### Post by philinux on 2008-11-12
You might like to try this gui. It's really good for tweaking stuff

[http://ubuntu-tweak.googlecode.com/files/ubuntu-tweak_0.4.0.1-1%7Eppa1_all.deb](http://ubuntu-tweak.googlecode.com/files/ubuntu-tweak_0.4.0.1-1%7Eppa1_all.deb)

---

