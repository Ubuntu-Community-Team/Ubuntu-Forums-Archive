---
title: "Ati proprietary driver: set powerstate=1 at boot"
date: 2008-11-23
forum: Hardware
---

### Post by raymanrt on 2008-11-23
Hi all,
 I've just learned how to change the power state of my VGA (Ati mobility x1600 with proprietary drivers on ubuntu 8.10) with the command: aticonfig --set-powerstate=1 . I really don't need frequently the powerstate=3 so I'm asking how is possible to make the default power state for my VGA the less consuming one.

Thank you,
   Riccardo

---

### Post by iggykoopa on 2008-11-23
you could make a shell script to change it and put it in your session.

just put:
aticonfig --set-powerstate 1
in a file and name it powerchange.sh or whatever. then:
chmod +x powerchange.sh
then go to system->preferences->sessions and add it as a startup program.

---

### Post by raymanrt on 2008-11-24
It's not what I thought but it's a good idea.
Thank you!

---

