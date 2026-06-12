---
title: "Unable to add Nautilus to Applications menu"
date: 2008-10-06
forum: General Help
---

### Post by Oldhacker on 2008-10-06
I right clicked on Applications to edit the menu with the intention of adding Nautilus. Nautilus is installed and runs when accessed from a terminal. However, even after selecting Nautilus and clicking the "show" box on System Tools, it does not appear on the menu. Is there something else that I must do?

Thanks,

---

### Post by haydnc on 2008-10-06
It could just be that the panel / menus needs to be forced to refresh.

I believe you can do it by opening up a terminal and typing:

```
sudo killall gnome-panel
```

You should see the panels disappear and then reappear, hopefully that'll sort you out.

---

### Post by Oldhacker on 2008-10-06
Thanks for the good try, but it did not help. :(
The panels disappeared and reappeared, but the menu remained unchanged without Nautilus.

---

### Post by haydnc on 2008-10-06
I don't have access to my Ubuntu machine at the moment so I can't be sure, but I seem to remember Nautilus appearing in the menus as 'file manager' or something similar rather than actually being listed as "Nautilus".

You don't by any chance see something like that listed there do you?

---

### Post by Oldhacker on 2008-10-06
There is a PCMan File Manager, which I already have on the menu.
However, I rather like the look and feel of Nautilus better.

---

### Post by haydnc on 2008-10-06
If no-one else gets there first I'll take a look when I get back to my Ubuntu machine later today.

What version are you running?

---

### Post by Oldhacker on 2008-10-06
I am running the 64 bit UBUNTU v8.04

---

### Post by lswb on 2008-10-06
I looked at my menu editor app and see "file browser" available to add to Applications/accessories, but since it defaults to opening my home directory, it is no different from using Main Menu/Places/Home Folder. If you still want it installed at Main Menu/Applications/System Tools you can add it as a new item, copying the settings from its entry under Apps/accessories.

---

