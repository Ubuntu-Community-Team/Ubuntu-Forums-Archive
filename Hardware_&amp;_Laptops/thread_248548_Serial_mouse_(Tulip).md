---
title: "Serial mouse (Tulip)"
date: 2006-09-01
forum: Hardware &amp; Laptops
---

### Post by Timothy Butwinick on 2006-09-01
Hello.
I downloaded Dapper Drake today in order to try it out. The problem is: I can't, because my serial mouse (from Tulip computers) does not work. Previously, I tried to install Slackware, but I experienced the same problem, however: only when I used X, bash worked fine with it (it wasn't very useful there, though). I cannot use a PS/2 mouse, since that port is broken. 
Is there a way to make it work, or do I have to buy an USB mouse?

I would also like to know some shortcut keys so I can turn the thing off without pulling the plug.

---

### Post by Timothy Butwinick on 2006-09-01
Problem solved: The trick was to change the /etc/X11/xorg.conf file, as explained [here]("http://www.ubuntux.org/problems-running-live-cd").

---

