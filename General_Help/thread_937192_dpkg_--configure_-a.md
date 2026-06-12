---
title: "dpkg --configure -a??"
date: 2008-10-03
forum: General Help
---

### Post by HelloEverybody77 on 2008-10-03
Ok, I'm very new here, and I have a question. I've been trying to install gtk-recordmydesktop on my ubuntu8.04. But whenever I choose to add the addplication this pops up!:( :confused:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried entering dpkg --configure -a into the terminal which asked me to go superuser. And for some reason that didn't work...

Help please. Thank you.

---

### Post by Ryadt on 2008-10-03
To gain superuser privilege use sudo
```
sudo dpkg --configure -a
```

---

### Post by howefield on 2008-10-03
How did you go superuser ?

Did you type the following into terminal

```
sudo dpkg --configure -a
```

---

### Post by HelloEverybody77 on 2008-10-03
Thanks, it worked! :D

I had been using acer aspire one before, and I kept shoving SU into the terminal.

---

