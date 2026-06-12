---
title: "Flash player on Opera 9.5"
date: 2008-07-26
forum: General Help
---

### Post by HpZ on 2008-07-26
Can someone please give me a simply step-by-step guide on how to install flash player on Opera 9.5?

TY

---

### Post by jonian_g on 2008-07-26
Have you installed the flash plugin from the repositories?

---

### Post by perlluver on 2008-07-26
Applications>Accescories>Terminal ```
sudo apt-get install flashplugin-nonfree
```

---

### Post by HpZ on 2008-07-26
so thats it? its now installed?

---

### Post by jonian_g on 2008-07-26
Yep. If it doesn't work there is a workaround.

---

### Post by carl_pr on 2008-07-26
i installed flash player 10 beta and opera 9.5 didnt had access to the plugin.

when i installed flash it installed in 

```
home/.mozilla/plugins/
```

and opera use this directory

```
usr/lib/mozilla/plugins/
```

i just opened nautilus as root and copy and pasted libflashplayer.so into

```
usr/lib/mozilla/plugins/ 
```

and that solved it.I dont know if this is your case or not but if you install flash 9 from the repositories i don't think you will have a problem at all.

---

