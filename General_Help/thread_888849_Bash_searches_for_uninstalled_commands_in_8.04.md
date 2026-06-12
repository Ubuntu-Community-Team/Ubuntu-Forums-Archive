---
title: "Bash searches for uninstalled commands in 8.04"
date: 2008-08-13
forum: General Help
---

### Post by endfx on 2008-08-13
I noticed that when you type a command that doesn't exist, bash tries to find the packages that command comes from and gives you a recommendation if that command is found in a package.

Is there a way to turn that off? I find it adds some lag on slower systems.

---

### Post by decoherence on 2008-08-13
```
sudo apt-get remove command-not-found
```

---

