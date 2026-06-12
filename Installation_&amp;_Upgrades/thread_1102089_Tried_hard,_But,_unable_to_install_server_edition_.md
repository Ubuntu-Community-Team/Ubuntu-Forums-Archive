---
title: "Tried hard, But, unable to install server edition !"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by kannalu45 on 2009-03-21
):P
Dear members,
I have downloaded server edition, wondered, that, from now on i won't be worried about viruses, 
while i was installing,  installation was done in command prompt with no graphical interface, but i hoped at the end i would be able to see a graphical interface of ubuntu,after ,I have done with my installation, I'm unable to see the graphical interface. Every time it makes me to login in command prompt only. I don't know what might be the reasons, as i'm new ,even i'm unable to give a connection to internet to seek for help from u, now i have formatted and using xp,
but i would like to know the reasons (WHY IT HAPPENED IN COMMAND PROMPT RATHER THAN IN GRAPHICAL(ORANGE)) COLOR.

Thank u,

Ravi.

---

### Post by oldos2er on 2009-03-21
The server version has no GUI, but you can install one by running 
```
sudo aptitude update && sudo aptitude install ubuntu-desktop
```
This will install Gnome.

---

### Post by namaku0 on 2009-03-21
Ummm...because you don't need GUI for a Linux server.
The bigger question is: Why would you run a server with a
Graphical User Interface?




BTW, in case you don't know yet, by default X/GUI isn't
part of Ubuntu server.
[https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq) (Q 1.4)

---

