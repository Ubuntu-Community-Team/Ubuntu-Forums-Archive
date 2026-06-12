---
title: "stuck as password screen"
date: 2008-10-20
forum: General Help
---

### Post by luke9511 on 2008-10-20
hello all i hope your all well, i just install ubuntu on a computer for my grandfather and for the first couple of days it was fine, but now for some reason it will not log in, it will get to the password screen and you type the password and hit enter and it just stays stuck there, after a while not sure how long, but it finally gets to the desktop, any ideas of what might be causing this? thanks in advance

---

### Post by phidia on 2008-10-20
The system was working fine before this happened?

You state that it will finally get to the desktop. You can check the Log Files from System > Administration. You can also open a terminal from Applications > Accessories and type "ps" to see if something is using a lot of cpu cycles.

It probably is a good idea to include the computer specs and the version of ubuntu you have installed.

---

### Post by luke9511 on 2008-10-20
> **phidia said:**
> The system was working fine before this happened?

You state that it will finally get to the desktop. You can check the Log Files from System > Administration. You can also open a terminal from Applications > Accessories and type "ps" to see if something is using a lot of cpu cycles.

It probably is a good idea to include the computer specs and the version of ubuntu you have installed.

its ubuntu 8.04, 1.2ghz with 384mb of ram i think im not sure i cant remember and i also have a hard time finding hardware window, theres alot of logs and i dont know what im looking for really in the logs, ps doesnt really say much just this

```
jack@ronald-desktop:~$ ps
  PID TTY          TIME CMD
 9283 pts/0    00:00:00 bash
 9302 pts/0    00:00:00 ps

```

---

### Post by luke9511 on 2008-10-21
anyone?

---

### Post by Monotoko on 2008-10-21
I think its the amount of RAM and the CPU speed, ubuntu will struggle to run on that little ram, either upgrade your RAM, or use xubuntu: [http://www.xubuntu.org/](http://www.xubuntu.org/)

Xubuntu is a lighter version of ubuntu and is designed torun on low spec machines such as you grandfathers :)

Btw, your grandfather is awesome for using Ubuntu :)

---

### Post by luke9511 on 2008-10-22
> **Monotoko said:**
> I think its the amount of RAM and the CPU speed, ubuntu will struggle to run on that little ram, either upgrade your RAM, or use xubuntu: [http://www.xubuntu.org/](http://www.xubuntu.org/)

Xubuntu is a lighter version of ubuntu and is designed torun on low spec machines such as you grandfathers :)

Btw, your grandfather is awesome for using Ubuntu :)

i have run ubuntu on a system with that same ammount or a little less and never had a problem before, its gotta be something else or something simple

---

