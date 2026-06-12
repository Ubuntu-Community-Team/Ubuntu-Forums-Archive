---
title: "help with flash player"
date: 2008-08-15
forum: General Help
---

### Post by jsalas8 on 2008-08-15
i'm trying to get adobe flash player on my system. i tried searching for it in synaptic packages and it seems i dont have it there. how can i get it?

---

### Post by kevstar31 on 2008-08-15
What browser are you using?

---

### Post by jsalas8 on 2008-08-15
mozilla firefox

---

### Post by dodle on 2008-08-15
Add (or enable) the Universe and Multiverse repositories to your /etc/apt/sources.list:> deb [http://mirrors.kernel.org/ubuntu](http://mirrors.kernel.org/ubuntu) hardy-updates main universe
deb [http://mirrors.kernel.org/ubuntu](http://mirrors.kernel.org/ubuntu) hardy-updates main multiverseThen go to a terminal:```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
sudo apt-get install libflash-mozplugin
```

---

