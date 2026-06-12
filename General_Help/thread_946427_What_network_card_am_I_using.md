---
title: "What network card am I using?"
date: 2008-10-13
forum: General Help
---

### Post by Valok on 2008-10-13
So I just installed Vbox, but the windows system doesn't come with drivers for my ethernet card.  But I can't find out what ethernet card I'm using from windows or from ubuntu.  Anyone know how you can find system specs in Ubuntu?

---

### Post by justleen on 2008-10-13
```

sudo lshw -short 
or
sudo lshw -short |grep network
or
sudo lshw -C network


```

---

