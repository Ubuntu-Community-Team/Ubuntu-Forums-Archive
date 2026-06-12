---
title: "Fast User Switch problems after 8.10 to 9.04 upgrade"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by jlappetito on 2009-07-24
I did an upgrade from 8.10 to 9.04 a couple of months ago. The upgrade was successful except that the Fast User Switch app is not working - at least the options that I use are not working. Specifically, Logout, Restart and Shutdown are not working. I get a prompt confirming the selection and an option to execute immediately, but clicking the Logout/Restart/Shutdown immediate button does nothing. If I wait for the clock to count down to zero, still nothing.

I have been using a terminal and using sudo shutdown etc. to restart and shutdown. Which works fine.

Another, problem is the root terminal app from the system tools menu doesn't work. I select "root terminal" and nothing happens.

Since both of these apps require root authority to work, it makes me think that is the problem.  I don't know how to figure out what the underlying commands for these apps are. Otherwise I would try to debug them myself.

Does anyone have any quesses as to what is going on here?

---

