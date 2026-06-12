---
title: "[SOLVED] getting 'out of range' messege on startup"
date: 2008-07-27
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2008-07-27
Hello every one.  My machine has been in storage for over a year(gutsy) Today, when I set it up and turned it on, it did a force check of disk as it said machine hasn't been checked in 383 days. that went ok. so when i booted it again, the orange bar goes across then I get a message **out of range** then a couple sets of numnbers **80 okmz **or some thing like that, (it goes away quickly) then machine will not finish booting. Can some one tell me what may be going on and how to "cure" it? Thanks

---

### Post by ryanhaigh on 2008-07-27
It sounds like your graphics settings aren't working with the monitor you are currently using. You can switch to the terminal (CTRL+ALT+F1) then use the command below to reconfigure your graphics.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by IusedTObeSOMEONEelse on 2008-07-27
thanks, got it

---

