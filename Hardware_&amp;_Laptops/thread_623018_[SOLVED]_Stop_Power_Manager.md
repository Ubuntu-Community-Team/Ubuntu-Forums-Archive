---
title: "[SOLVED] Stop Power Manager"
date: 2007-11-25
forum: Hardware &amp; Laptops
---

### Post by viking777 on 2007-11-25
How do I stop the 'power manager' program from starting in KDE?

It is a complete waste of resources starting it since all it promises to do is to suspend or shutdown the laptop and since it is utterly incapable of doing either it is not worth starting.

I went through all the run levels in /etc/rc0.d to /rcS.d and it is not there, neither is it in .kde/Autostart. 

I also tried quitting the program and saving the session, but that doesn't work either.


So where does it start from and how do I stop it from loading?

---

### Post by viking777 on 2007-11-26
SOLVED. (sort of)

I couldn't find out how to stop it from starting so I did the next best thing which was to remove it altogether. 

The trick to that is finding out what it is called. Although the program calls itself 'Power Manager', you will search in vain for that. In fact it is called 'kde-guidance-powermanager' just to make things easier for you:mad:

Remove it and I have shaved a couple of seconds off my boot up time which was the point of the exercise.

---

