---
title: "[SOLVED] Trouble installing Adobe Flashplayer"
date: 2008-08-22
forum: General Help
---

### Post by vegas588 on 2008-08-22
I am trying to install adobe flashplayer but I am getting this error message:

jamesc@hpubuntu:~/Documents$ ls
flashplayer-installer  install_flash_player_9_linux  libflashplayer.so
jamesc@hpubuntu:~/Documents$ ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

jamesc@hpubuntu:~/Documents$ 


Is there another flash player for my architecture or how else can I install flash?

---

### Post by LateNiteTV on 2008-08-22
did you try installing it thru synaptec package manager?

---

### Post by WRDN on 2008-08-22
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by aysiu on 2008-08-22
> **vegas588 said:**
> 
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

jamesc@hpubuntu:~/Documents$  If you're using 64-bit, you'll have to employ a workaround, as your architecture is not supported.

Try [this](http://ubuntuforums.org/showthread.php?p=1174435)

---

### Post by LateNiteTV on 2008-08-22
just install it thru synaptec and it will work.

---

### Post by aysiu on 2008-08-22
> **LateNiteTV said:**
> just install it thru synaptec and it will work.
Even in 64-bit Ubuntu?

---

### Post by LateNiteTV on 2008-08-22
> **aysiu said:**
> Even in 64-bit Ubuntu?

yes.

---

### Post by vegas588 on 2008-08-22
What exactly am I looking for in synaptic? I am new to this, so I am not sure what to look for. Thanks.

---

### Post by vegas588 on 2008-08-22
i found what i was lookin for in synaptic. sorry. I will try that installation and report back when it finishes.

---

### Post by vegas588 on 2008-08-22
That worked. great! AMD Turion64X2. 

Thanks.

---

