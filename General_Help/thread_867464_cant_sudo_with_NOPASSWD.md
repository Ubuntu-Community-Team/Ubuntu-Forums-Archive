---
title: "cant sudo with NOPASSWD"
date: 2008-07-22
forum: General Help
---

### Post by mdsharp24 on 2008-07-22
I just changed /etc/sudoers using visudo to reflect:

%sudo ALL = NOPASSWD: ALL

and added my login (michael) to the group sudo:

sudo:x:27:michael

yet I am still unable to sudo to any root cmd without a password. What am I missing?

---

### Post by Dr Small on 2008-07-22
Try:
```
%sudo ALL=(ALL) NOPASSWD: ALL
```

Also, once you added yourself to the 'sudo' group, did you logout and log back in for it to change groups?

---

### Post by mdsharp24 on 2008-07-22
%sudo ALL=(ALL) NOPASSWD: ALL  (using visudo)
sudo:X:27:michael

rebooted, then:  sudo apt-get update

and it asks for password  :(

---

