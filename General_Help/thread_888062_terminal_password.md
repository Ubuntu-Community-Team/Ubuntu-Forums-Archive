---
title: "terminal password"
date: 2008-08-12
forum: General Help
---

### Post by stkblazer on 2008-08-12
when i do a sudo command in the terminal it asks me for my password i put it in but nothing happens and it wont let me continue like i hit the keys and nothing goes into the terminal im on ubuntu 8.04 hardy

---

### Post by sisco311 on 2008-08-12
You just aren't getting any visual feedback.
Just type your password and hit Enter.

[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by tuxxy on 2008-08-12
Your password will not be displayed for security reasons, it is working though, enter password and hit enter

---

### Post by ilrudie on 2008-08-13
This is a pretty common problem I see on the forums from green users.  Perhaps we should make the default sudo behavior in Intrepid lecture users about how to enter passwords in the terminal.  something like
```
When typing your password in the Terminal you will not receive visual feedback.
Just type your password normally and hit enter.
To remove this message edit the sudoers file with sudo visudo and change the line
Defaults lecture=always,lecture_file=/etc/sudolecture to 
Defaults !lecture 
```

---

