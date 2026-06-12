---
title: "Aiglx or Fglrx"
date: 2007-11-22
forum: Hardware &amp; Laptops
---

### Post by Loki1989 on 2007-11-22
Which is better and how would on enable the better on an Nvidia GeForce 7300 GS???

---

### Post by Jouke74 on 2007-11-22
AIGLX is generally better (best of the worse) and you enable this by downloading and installing the restricted drivers. Subsequently yu might need to check your Xorg.conf if everything is ok. A program that may help with both steps to do it automagically for you is Envy.

Fglrx is the videocard driver for ATI cards, you better stay away from that.

(and basically also ATI owners if they can :lolflag:)

Then there is is still XGL which you cannot use of AIGLX. There is no need to run XGL for Nvidia owners as the AIGLX should work fine. If not, then there is usually something wrong with the configuration of files.

---

### Post by Loki1989 on 2007-11-22
thanks man got envy going and ti works great now but I was also wondering how do I check it if is running aiglx?

---

### Post by Jouke74 on 2007-11-22
Ehhhh.. should say something like  AIGLX "On" on your xorg.conf file under /etc/X11/. But if it was not working, you would not write that things are going great....

---

