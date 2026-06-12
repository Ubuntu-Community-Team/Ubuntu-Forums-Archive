---
title: "cant find .emacs file"
date: 2008-08-27
forum: General Help
---

### Post by kcode on 2008-08-27
i want my tab identation from 4 to 8 (in emacs), for which i learned that i need to edit my ~/.emacs file. i cant find it. i tried _locate .emacs_ but it didnt show up the file.

thanks

---

### Post by monkeyking on 2008-08-27
Just put your stuff In a new .emacs file in your home dir.

The systemwide emacs setup isn't called .emacs

---

### Post by Dr Small on 2008-08-27
(Notice! I am not an emacs user)
The systemwide emacs configuration file should be located at:
```
/etc/emacs
```

Your custom emacs file should be located at:
```
~/.emacs
```

If it does not exist, just create it.

Dr Small

---

### Post by kcode on 2008-08-27
got you.

---

