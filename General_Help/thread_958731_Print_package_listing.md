---
title: "Print package listing"
date: 2008-10-25
forum: General Help
---

### Post by indiekid97 on 2008-10-25
Thanks in advance to all who reply :],
I was wondering if there was a way to print all of the installed packages on my machine into the terminal?

---

### Post by jerome1232 on 2008-10-25
That ought to get it for you.

```
dpkg --get-selections | grep -v deinstall
# or if you wanted it in a text file for later viewing
dpkg --get-selections | grep -v deinstall > installed-packages.list
```

edit: Actually while searching around I found [this]("http://ubuntuforums.org/showthread.php?p=1990911") post that has a way to install them again using the text file that is generated.

---

### Post by indiekid97 on 2008-10-25
Thanks 10^6, that's just what I was looking for. I'm in the process of doing a full reinstallation to intrepid, but didn't want to reinstall pesky applications (awn-bzr anyone?).

---

