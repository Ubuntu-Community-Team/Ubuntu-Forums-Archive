---
title: "[SOLVED] Installed Flash 10 now it says I have Flash 9 and 10 installed"
date: 2008-10-15
forum: General Help
---

### Post by Zzzach on 2008-10-15
I installed Flash 10 today from the Adobe site but when I go to about:plugins in firefox it lists both flash 9 and flash 10. I search synaptic but it didn't show flash 9 installed so how do I get rid of it? I went in my mozilla plugin folder and there is only one libflashplayer file. :confused:

---

### Post by McQuaid on 2008-10-15
That's probably your problem.  You shouldn't really have any plugins in YOUR home mozilla folder.  The plugin is installed system wide.  

Remove that (or move it to be safe) restart firefox and you should be good.

---

### Post by Yellow Pasque on 2008-10-15
This should remove your Flash 9 install:
```
sudo apt-get remove flashplugin-nonfree
```

---

### Post by Zzzach on 2008-10-17
> **McQuaid said:**
> That's probably your problem.  You shouldn't really have any plugins in YOUR home mozilla folder.  The plugin is installed system wide.  

Remove that (or move it to be safe) restart firefox and you should be good.

Thanks... I deleted that and it only lists Flash 10 now so it looks like that fixed it.

---

