---
title: "display current kernel on launch panel"
date: 2008-08-24
forum: General Help
---

### Post by SpaceMaster on 2008-08-24
This may sound silly....

But what would I need to do to display the currently loaded kernel on the panel?  I just want a simple "linux 2.6.xx".  

I've figured as far as the right click on the panel -> +add to panel, but don't know exactly how I should approach it after this step.

---

### Post by Gourgi on 2008-08-24
you can view your kernel's version from system monitor if you want.
i don't think there is a panel-applet for what you are asking though

---

### Post by SpaceMaster on 2008-08-24
yeah, but the system monitor requires clicking my mouse once.  sometimes twice.

Perhaps I could craft a simple little stream that reads the name of the currently loaded kernel, and outputs it to a file, then display the file's contents on the launcher.

I guess what I'd need for that is to find from where the terminal gets that info.

---

### Post by pauper on 2008-08-24
> I guess what I'd need for that is to find from where the terminal gets
that info.
```
uname -sr
awk '{print $1, $3}' /proc/version
```

---

### Post by SpaceMaster on 2008-08-25
Awesome Possum!

Thank you gentle sir.

---

### Post by sayakb on 2008-08-25
Please mark the thread as solved.

---

