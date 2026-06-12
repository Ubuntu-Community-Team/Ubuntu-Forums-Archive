---
title: "[SOLVED] No sudo user on entire machine"
date: 2008-11-12
forum: General Help
---

### Post by leehach on 2008-11-12
I just did something very stupid.  I added myself to a group using ```
usermod -G [newgroup] lee
```  Without the -a option, newgroup *replaces* all other groups.  This  means I got kicked out of sudoers or whatever group I need to sudo.  There are no other users with sudo privileges on my computer.  How can I make myself an administrative user if I don't have administrative privileges?

Aggh!

---

### Post by SuperSonic4 on 2008-11-12
Restarting in safe mode will give you a terminal as root I believe.

---

### Post by sisco311 on 2008-11-12
reboot in recovery mode and add your user to the admin group from the root shell:
```
adduser *username* admin
```

next time use the -a flag(append):
```
usermod -**a**G *group1[,group2...]* *username*
```

---

### Post by leehach on 2008-11-13
Thanks, this is great.

---

