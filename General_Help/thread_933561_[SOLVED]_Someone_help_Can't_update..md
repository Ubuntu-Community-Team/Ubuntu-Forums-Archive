---
title: "[SOLVED] Someone help? Can't update."
date: 2008-09-29
forum: General Help
---

### Post by BeauBridges on 2008-09-29
I get this error when I try to restart:


[IMG]http://i38.tinypic.com/dy3bxf.png[/IMG]

Someone help?

---

### Post by jf812 on 2008-09-29
1:can you tell me where you got that theme thingy with buttons at bottom because i like!

2: before you put the command put sudo a space then the command.

e.g sudo reboot. Then i might ask for your password. Then hey presto you're away!

---

### Post by Titan8990 on 2008-09-29
Close the update manager and try:

sudo dpkg --configure -a

---

### Post by Titan8990 on 2008-09-29
> 1:can you tell me where you got that theme thingy with buttons at 
bottom because i like!


sudo apt-get install avant-window-navigator

---

### Post by BeauBridges on 2008-09-29
Problem solved :D

Thanks guys.

---

### Post by Titan8990 on 2008-09-29
Good to hear. Don't forget to mark it as solved via thread tools at the top.

---

### Post by jf812 on 2008-09-29
A bit off-topic but why is the command called sudo?

---

### Post by Titan8990 on 2008-09-29
From Wikipedia:

"The sudo (super user do; officially pronounced /&#712;su&#720;du&#720;/,[2] though /&#712;su&#720;do&#650;/ is also common) command is a program for Unix-like computer operating systems that allows users to run programs with the security privileges of another user (normally the superuser)."

In non-debian based distros you would "su" (super user) to log in to root and then perform your administrative tasks.

---

### Post by jf812 on 2008-09-30
ahhhhhhhhh. Thanks

---

