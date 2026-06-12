---
title: "installing fonts?"
date: 2008-07-27
forum: General Help
---

### Post by Exile666 on 2008-07-27
I wanted to know how to install fonts in Ubuntu, but for some reason(call me blond if you will) i didn't understand any of the tutorials, Ubuntu n00b is what i am. Eventually i came across a tutorial that said Nuatilus file manager was the best way by using 'Fonts:///'. But he said nothing on installing it, and when i checked the synaptic package manager, it was already installed. So what do i do? if it helps its a .ttf file.

---

### Post by Vadi on 2008-07-27
Try this.

Go to Places - Home Folder.
Press Ctrl+H
Press Ctrl+Shift+N, and name the new folder ".fonts"
Place the .ttf font in that folder. Logout, log back in, and the font should be accessible.

---

### Post by Kevbert on 2008-07-27
Instead of logging out and back in, put the ttf in your newly created .fonts folder and the from terminal enter
```
sudo fc-cache -fv
```

---

### Post by nikgare on 2008-07-27
This might help:
[https://wiki.ubuntu.com/Fonts#head-51423ff7185d56b59d892cfc5af4fd0cffb7073d](https://wiki.ubuntu.com/Fonts#head-51423ff7185d56b59d892cfc5af4fd0cffb7073d)

---

