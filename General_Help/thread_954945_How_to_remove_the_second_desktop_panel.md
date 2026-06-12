---
title: "How to remove the second desktop panel?"
date: 2008-10-21
forum: General Help
---

### Post by Pagh on 2008-10-21
Hey everyone.

By default Gnome (in Ubuntu 8.4) comes with two panels - for some reason however one is only able to delete one of them by right clicking on it and choose the "delete this panel" option. 

So my question is: Is it possible to delete both panels and say only use a dock or whatever instead.

All the best Kasper Roland Pagh.

---

### Post by loomsen on 2008-10-21
Hi

I describe it [HERE](http://ubuntuforums.org/showpost.php?p=5691394&postcount=39)

Part II you can find in my sig. 

You can't delete it because gnome specifies nautilus(file manager), metacity(it was I think as the window manager) and the gnome-panel as it's panel.

In Intrepid there's a gconf key called requiured components. However, it's still possible... Read above.

---

### Post by pirattrev on 2008-10-23
I'd be careful with loomsen's suggestion, it involves some stuff that could cause you problem's later if you don't know how to undo them.  so, know what you're doing well before following any suggestion that prompts you to remove a filemanager if you don't know the cli way to get it back.

---

### Post by posburn on 2008-10-23
You do not need to remove Nautilus.  Open up system->preferences->sessions.  In the first tab, "Startup Programs" remove the entry for gnome-panel.  This will prevent it from autostarting when you reboot.  Then go to the "Current Session" tab, select the gnome-panel entry in the list and click "remove".  That should kill the current instance of the panel.

---

