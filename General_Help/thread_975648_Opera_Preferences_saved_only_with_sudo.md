---
title: "Opera Preferences saved only with sudo"
date: 2008-11-08
forum: General Help
---

### Post by blingo on 2008-11-08
Opera Preferences aren't saved, except when I run it with sudo.
It doesn't throw an error or something, just don't save.
Any thoughts?

---

### Post by aysiu on 2008-11-08
**Step 1**
Close all instances of Opera

**Step 2**
Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R $USER:$USER ~/.opera
```

**Step 3**
Start Opera again and see if your preferences are saved

Don't run graphical applications with *sudo*. More details [here](http://www.psychocats.net/ubuntu/graphicalsudo).

---

