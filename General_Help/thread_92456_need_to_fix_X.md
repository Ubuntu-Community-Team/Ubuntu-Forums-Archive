---
title: "need to fix X"
date: 2005-11-19
forum: General Help
---

### Post by chronusdark on 2005-11-19
ok i was trying to get twinview to work when i accidentally overwrote my /etc/X11/X file now x wont start, is there a way to reinstall it? this is driving me nuts and im on the verge of a nervous breakdown

thanks - ChronusDark

---

### Post by invalid on 2005-11-19
```
sudo dpkg-reconfigure xserver-xorg
```

Cheers,
Cb

---

### Post by az on 2005-11-19
Actually, try

sudo apt-get install --reinstall xserver-xorg-core

---

### Post by invalid on 2005-11-19
[QUOTE=azz]Actually, try

sudo apt-get install --reinstall xserver-xorg-core[/QUOTE]
Ah I am sorry, I misread the original post. This is the correct thing to try.

Sorry,
Cb

---

### Post by chronusdark on 2005-11-20
well i fixed it actually all i did was delete a symlink
its good now but thanks for the responses

---

