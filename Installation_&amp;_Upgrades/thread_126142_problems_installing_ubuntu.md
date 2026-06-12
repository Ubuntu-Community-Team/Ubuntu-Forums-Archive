---
title: "problems installing ubuntu"
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by runeri on 2006-02-05
Hi there.

i just installed ubuntu on my old pc.
now i rune the first time boot. ubuntu is making it through the loading moduls procedure, with the ubundu logo in top. after that, it just freezes.
any one knows what's wrong??

Rune, denmark

---

### Post by dcast on 2006-02-05
where does it freeze? what does it look like? more information?

---

### Post by runeri on 2006-02-05
it freezez right after all modules have been loaded. 
just a black screen, with little white cursor in the upper left corner.
i can reach some promt by pressing alt+ctrl+f1, but don't know what to do there.

---

### Post by dcast on 2006-02-05
thats a command prompt not frozen does it say login? if so login with your name and password you created? what type of install did you do? normal or server?

---

### Post by runeri on 2006-02-05
i did normal install.
i can make the login with the login i have made during the install, but then what?

---

### Post by dcast on 2006-02-05
try typing "startx" then hitting enter. If that fails try "sudo dpkg-reconfigure xserver-xorg" and enter the password that you created.

---

### Post by runeri on 2006-02-05
seems to be my graphic card that's the problem....
its a good old MX400L64T POINT OF VIEW 64MB, what should i choose for that in the menu?

---

### Post by runeri on 2006-02-05
fatal server error:
server is already active for display 0
if this server is no longer running, remove /tmp/.x0-lock
and start again

whats that now?

---

### Post by runeri on 2006-02-06
please help.....
i'm close to the edge now!!!!!

---

