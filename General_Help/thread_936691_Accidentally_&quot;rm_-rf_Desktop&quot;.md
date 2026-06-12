---
title: "Accidentally &quot;rm -rf Desktop&quot;"
date: 2008-10-03
forum: General Help
---

### Post by evillan on 2008-10-03
I accidentally "rm -rf" my Desktop/ directory (which isn't that bad since I had copies of all the files). 

The problem is; after i restarted my laptop, everything in my home directory got displayed on my desktop (as if I've move my home dir to Desktop/).
I tried to "mkdir Desktop" and reboot, that didn't help.

What should I do?

---

### Post by Elfy on 2008-10-03
From Alt+F2 run gconf-editor - navigate to /apps/nautilus/preferences and remove check from Desktop_is_home_dir

---

### Post by russlar on 2008-10-03
> **evillan said:**
> I accidentally "rm -rf" my Desktop/ directory (which isn't that bad since I had copies of all the files). 

The problem is; after i restarted my laptop, everything in my home directory got displayed on my desktop (as if I've move my home dir to Desktop/).
I tried to "mkdir Desktop" and reboot, that didn't help.

What should I do?

Did it show hidden files?

---

### Post by evillan on 2008-10-04
> **forestpixie said:**
> From Alt+F2 run gconf-editor - navigate to /apps/nautilus/preferences and remove check from Desktop_is_home_dir
It was already unchecked. I tried to check it, reboot, uncheck it and reboot again, but that didn't help

> **russlar said:**
> Did it show hidden files?

Which one? The Desktop/ dir?

Could one of you write the write/read/execute-permission for the Desktop dir? Could that be the problem?

---

