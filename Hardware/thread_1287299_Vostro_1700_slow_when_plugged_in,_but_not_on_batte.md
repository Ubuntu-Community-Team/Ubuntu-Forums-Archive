---
title: "Vostro 1700 slow when plugged in, but not on battery"
date: 2009-10-10
forum: Hardware
---

### Post by viralin on 2009-10-10
I have a friend's laptop that is a Dell Vostro 1700 laptop that started running really slow.  The cpu seems to be peaked out whenever anything opens.  Startup times have increased from less than 30 sec to over 4 min.  Everything is jerky and slow to respond.  But the kicker is that if you pull the power cord and run it on battery it's perfect, everything works flawlessly and very fast.  I have never seen this before and don't even know where to start.  I'm fairly new to linux, but not to computers.  Any suggestions would be greatly appreciated.

---

### Post by s3a on 2009-10-10
Is tracker indexing at high priority or something?

---

### Post by viralin on 2009-10-10
i don't see anything that resembles that in the process list.  does it have a specific name?

---

### Post by s3a on 2009-10-10
trackerd is the name in the processes list but you could find the problem by entering the "top" command whenever you experience the problem to see what is using up the ressources and we can work on it from there.

---

### Post by viralin on 2009-10-10
well, running with top open and nothing else it bounces between 2-14% usually Xorg and top are the highest.  if i move the mouse pointer down to my awn manager, Xorg jumps to about 70%.  if i open something like firefox, i can see firefox using 99% for a little while and again bouncing between ff and Xorg.  if i do the same thing with the power unplugged, the same dance happens but Xorg only uses about 16% when moving by the awn manager and when ff opens it happens so quick the only thing i see is that ff uses about 23% then it's loaded.

---

