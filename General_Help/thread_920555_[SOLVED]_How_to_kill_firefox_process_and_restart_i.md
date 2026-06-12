---
title: "[SOLVED] How to kill firefox process and restart it in terminal?"
date: 2008-09-15
forum: General Help
---

### Post by crazyfuturamanoob on 2008-09-15
_How can I kill firefox process and restart it in terminal?_

And how to make alias for those commands too? Thanks.

---

### Post by Steve1961 on 2008-09-15
> **crazyfuturamanoob said:**
> _How can I kill firefox process and restart it in terminal?_

And how to make alias for those commands too? Thanks.

killall firefox
firefox

to make alias command just edit your ~/.bashrc file and add entries such as:

alias whateveryouwant='killall firefox'

Not exactly necessary though as the commands are short anyway

---

### Post by Oldsoldier2003 on 2008-09-15
I would do:
```
killall firefox && nohup firefox > /dev/null
```
This allows you to close the terminal and sends the nohup.out file to dev null. 


edit: Without nohup, closing the terminal will close firefox.

---

### Post by crazyfuturamanoob on 2008-09-15
Thanks :D

Firefox often freezes, and when I close  it, there still exists a firefox process, 
which prevents me from starting new firefox process. 

So killing the old process and starting a new one solves the problem.

---

### Post by slimjimmy23 on 2009-11-25
This helped out alot, I'm new to Ubuntu and after I closed firefox it said it was still running, I then remembered the killall command so I googled 'killall firefox' and I stumbled upon this forum. :D  ---------------- Listening to: [Motley Crue - Live Wire](http://www.foxytunes.com/artist/motley+crue/track/live+wire)

---

