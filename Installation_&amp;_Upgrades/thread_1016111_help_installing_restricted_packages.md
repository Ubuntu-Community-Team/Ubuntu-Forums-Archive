---
title: "help installing restricted packages"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by meissler on 2008-12-19
Hey guys, new Ubuntu (8.10) user here.  I tried installing the restricted packages using sudo aptitude install ubuntu-restricted-extras but I'm having some trouble.  In the terminal, a Java screen came up with their terms and conditions I suppose, but I couldn't click anywhere so I exited the terminal.  Now I can't install the packages.  When I type in sudo aptitude install ubuntu-restricted-extras I get a message saying "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem:

Anyone know what to do?  Thanks.

---

### Post by Sealbhach on 2008-12-19
OK, first do as it suggests and run 

```
dpkg --configure -a
```

Then try to install restricted extras again. When you get to the Java license stuff, keep pressing Enter or else use the down arrow key to get to the end of the document, then press Y.... it goes something like that anyway. You can't use a mouse but you can use the keyboard to get to the end of it.



.

---

### Post by meissler on 2008-12-19
Got the Java screen again, but I can't get it away.  I keep pressing Y, enter, scrolled down and all.  What a pain...

---

### Post by meissler on 2008-12-19
Got it!  Tab then enter for anyone else trying to do it.

---

