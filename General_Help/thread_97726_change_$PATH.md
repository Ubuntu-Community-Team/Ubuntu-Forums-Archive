---
title: "change $PATH"
date: 2005-12-01
forum: General Help
---

### Post by not_yet on 2005-12-01
how and where is the $PATH changed:confused:

---

### Post by psychicdragon on 2005-12-01
You can add something to your path with a command like this:
```
PATH=/some/dir:$PATH
```
If you want the directory to always be in your $PATH (even after rebooting/logging-out), you should add this to your **~/.bashrc** and **~/.bash_profile** files:
```
PATH=/some/dir:$PATH
export PATH
```
This shows you what is currently in your $PATH:
```
echo $PATH
```

---

### Post by hove99 on 2005-12-24
Thanks for this reply, it solved my problem!
However, one should not add the lines to .bashrc , since this will cause the $PATH variable to contain your added path as many times as you open the terminal. Adding the lines to .bash_profile will solve the problem on its own.

---

