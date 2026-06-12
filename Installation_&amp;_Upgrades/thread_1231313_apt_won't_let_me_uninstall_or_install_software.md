---
title: "apt won't let me uninstall or install software"
date: 2009-08-04
forum: Installation &amp; Upgrades
---

### Post by }SoC{phenix on 2009-08-04
Hello, I recently went to remove a few apps that I am not longer using (memory hogs on an older system), and synaptic wouldn't uninstall all of them.  It now won't let me just uncheck the apps, and it won't install new programs until these are deleted.  Is there a way to reset apt so that it stops trying to uninstall this software?  I have enough disk space to just leave the programs there, they're not running or getting in the way.

The dialogue I got from synaptic is as follows:
E: knotes: subprocess post-removal script returned error exit status 2
E: korganizer: subprocess post-removal script returned error exit status 2
E: libkpgp4: subprocess post-removal script returned error exit status 2
E: libksieve4: subprocess post-removal script returned error exit status 2
E: libmimelib4: subprocess post-removal script returned error exit status 2

Yes I have tried unmark all, it doesn't do anything.

-}SoC{phenix

---

### Post by Maheriano on 2009-08-04
```
sudo apt-get remove <application-name>
```

---

### Post by }SoC{phenix on 2009-08-04
using apt-get remove simply returns the same errors except this time in the console.

---

### Post by Maheriano on 2009-08-04
Maybe I jumped the gun on my assumption that you searched the internet for what status 2 means on an exit.

---

### Post by }SoC{phenix on 2009-08-04
I honestly don't see anything about this issue from a google search, so I am asking here for help in finding the answer.

---

