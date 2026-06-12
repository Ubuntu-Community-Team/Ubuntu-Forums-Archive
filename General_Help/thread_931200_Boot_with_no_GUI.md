---
title: "Boot with no GUI"
date: 2008-09-27
forum: General Help
---

### Post by RunningBear on 2008-09-27
How do I boot Ubuntu 8.04.01 so that it starts with a command line rather than the Gnome GUI?

Thanks

_DAVID WARNER

---

### Post by Atomsmasher on 2008-09-27
Hey man, I was looking for a solution to my own problem when I came  across this.  It may help you out.

[http://ubuntuforums.org/showthread.php?t=929115](http://ubuntuforums.org/showthread.php?t=929115)

---

### Post by hyper_ch on 2008-09-27
```

sudo update-rc.d -f gdm remove

```

that will remove gdm from auto-starting and hence you'll be in the shell.

---

