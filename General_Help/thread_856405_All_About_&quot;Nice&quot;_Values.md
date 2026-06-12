---
title: "All About &quot;Nice&quot; Values"
date: 2008-07-11
forum: General Help
---

### Post by mikeyfbi on 2008-07-11
Hey Guys,

I was just looking at the priority options of SystemMonitor, Nice values.

I understand that if you lower them, you give higher priority, and raise them, you get a lower priority.

But to what degree?

Let's say I change the nice value of firefox and firefox-bin to -1.
(I'm not even sure what firefox-bin is tho :o)

How will this affect firefox's performance?  How will this affect the rest of my system?

What if I change them to -5?

If anyone could shed some light (in simple English:)) about nice values for myself and possibly others searching for the same thing, that would be 'nice'!

I've already started to play with it, to see if I notice anything, but I'd like to know what some experienced users have to say.

Thanks in advance,

Mike

---

### Post by hal8000 on 2008-07-11
Changing the renice value alters the priority of a task. You probably wont see much difference with firefox but more labour intensive tasks like updatedb may show improvement.

Heres the man page (if you want to read it online)
[http://linux.die.net/man/8/renice](http://linux.die.net/man/8/renice)

---

