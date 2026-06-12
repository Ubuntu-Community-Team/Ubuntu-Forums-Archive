---
title: "Problem after updating from 8.10 to 9.04"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by vern3219 on 2009-06-02
After updating from Ubuntu 8.10 to 9.04 unable to log in.

In 8.10 there was no need for a user name only the password. Now that I have updated to 9.04 it requires that I use a "user name and password". Since I do not have a user name in 8.10 it is impossible to log in, is there a solution to this?

Thank you
Clayton Stapleton

---

### Post by quixote on 2009-06-03
Your description of the 8.10 situation doesn't sound right.  Are you sure you didn't have automatic login turned on, in which case it wouldn't wait for either a username or password.  Then, later in the boot process when it tried to connect to your network, it asks you for the password to that.

If that's what's happening, then the jaunty upgrade has turned off automatic login.  (Probably some security featurette, so that you have to turn it on again consciously.)  

I think you must have had a login name because I'm not sure you can install ubuntu without one.  But if you really had no login name, then just hit return when it asks for one, and -- assuming the password screen comes up -- enter your ubuntu password.  (It might be the same as your network one, or not, depending how you set it up.)

Hope any of this helps!

---

### Post by merlinus on 2009-06-03
Your username would be your personal directory in /home.

---

### Post by quixote on 2009-06-03
Yeah.  I would think so too! ;-)

---

### Post by vern3219 on 2009-06-04
Thanks every one!
Solved the problem by going into "recover mode" and added a new user and password. Now I am able to access Ubuntu 9.04.

Thanks again
Clayton Stapleton

---

