---
title: "Configure Suspend command"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by azoele on 2007-03-27
Hello all,

I have finally switched to Ubuntu, and all my hardware seems to work in a nice way!
Even suspend works, only it needs tricks: suspend to disk works when I push
"Hibernate" on the exit menu of gnome, it goes off and restarts properly (even totem resumes playing!)

However, Suspend doesn't work... when resuming, I see no screen.
I have a Dell D800, which has always been infamous for this, but there's a trick that works.
Simply echoing
"echo mem >/sys/power/state"
suspends the computer, and on resume it works again like a charme...

How can I tell the graphical interface (the thing that appears when I click "System->Exit..." in Gnome simply issue that command when I click Suspend?
It is a waste to keep a root terminal open to issue it manually all the time...

Thanks a lot!

Lorenzo

---

