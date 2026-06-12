---
title: "reinstall after saving /home?"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by mfox on 2009-01-14
I'm running Ubuntu 8.04.1 with netbook remix and there is now a minor problem with the windows in all apps as a result of what I believe is a bug in one of the remix components.  I've filed a bug report for that component (Desktop-switcher), but would like to get my system back to the way it was right away.  So here is my question.  Can I save my /home folder, then wipe my Ubuntu Hardy volume on my laptop, reinstall Hardy from scratch and THEN, replace my old /home file (in place of the one created by the new installation)?  Could replacing the entire /home file cause some instability; e.g. because some of the Hardy files may have changed?  Is there a better procedure or a way to make sure it's OK before replacing?

---

### Post by unutbu on 2009-01-14
In general, what you describe works fine. However, if your current problem regarding Desktop-switcher is caused by a configuration file in your home directory, then copying it back after the reinstall well of course re-introduce the problem. 

So when you restore your /home directory, copy data files, but not the config files. (The config files all start with a dot in the file/directory name. E.g. ~/.gconf or ~/.gnome). 

Note that your bookmarks are in ~/.mozilla. You may want to copy that one over, especially if you believe it is not related to the Desktop-switcher problem.

---

### Post by kranny on 2009-01-14
```
cd ~
tar czvf backup.tar.gz ~/[a-zA-z]* ~/.mozilla
```

This is what you are looking for..

---

