---
title: "help installing items from &quot;add/remove&quot;"
date: 2008-09-10
forum: General Help
---

### Post by bradpurvis on 2008-09-10
every time i try to install software from the add/remove section in the applications section of the top panel i get this message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

so i am reporting this.

help please and thank you

---

### Post by fooman on 2008-09-10
have you tried running that command?  if not,  open a terminal and type or copy/paste the following into it:

```
sudo dpkg --configure -a
```

see if that helps.

---

### Post by sisco311 on 2008-09-10
open a terminal
(Applications -> Accessories -> Terminal)
and type (or copy/paste):
```
sudo dpkg --configure -a
```
insert your password and press Enter.

---

### Post by bradpurvis on 2008-09-10
i don't know why but when i put that in it started setting up google earth. lol. it is strangly working now thank you!

---

### Post by bradpurvis on 2008-09-10
um i have another question. is there any dock for ubuntu simaler to the mac os x dock or rocketdock for windows?

---

### Post by sisco311 on 2008-09-10
> **bradpurvis said:**
> um i have another question. is there any dock for ubuntu simaler to the mac os x dock or rocketdock for windows?
yes, awn:
[http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)

---

