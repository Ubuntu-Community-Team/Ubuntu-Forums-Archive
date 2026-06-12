---
title: "Without GDM, how to unlock admin  like [users-admin, services-admin]?"
date: 2008-11-29
forum: General Help
---

### Post by desper on 2008-11-29
Hi,

After GDM is disabled(then tty login and xinit), I am no longer able to unlock (button greys out) services like users-admin, services-admin. 

Is there anyway to bring those admin services back, without using gdm(kdm)?

Thanks and Regards,

desper

---

### Post by dnoyeb on 2010-03-24
This is a very good catch.  I am also having the users-admin problem.  I never noticed that it started after I stopped the gdm service.

If I use startx, I get the greyed out unlock button.  If I log in via gdm, then I do get the unlock button that is non-greyed.  I wonder if there is a bug report somewhere.

I'm using 9.04 Jaunty Jackalope.


I wonder if policy kit is using gdm somehow to tell if you are running locally or potentially remotely.

---

