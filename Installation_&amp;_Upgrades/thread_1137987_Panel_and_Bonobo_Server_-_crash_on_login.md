---
title: "Panel and Bonobo Server - crash on login"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by vishi on 2009-04-26
I upgraded from 8.10 and found that the panel crashes on login. I get a message:

The panel could not register with the bonobo-activation server (error code: 1) and will exit.It may be automatically restarted.

On checking the logs on /usr/var/messages, I found the following:

user.log:Apr 26 02:23:53 username-ubuntu bonobo-activation-server (username-6444): could not associate with desktop session: Failed to connect to socket /tmp/dbus-0awRqeCWk1: Connection refused

I tried uninstalling and reinstalling the panel and bonobo server. No use. 

I get a blank desktop screen when I login and I had a tough time figuring out how to launch Terminal. Once I got the terminal up, I could pen firefox and write this post. 

Hoping for a solution...:confused:

Thanks,
Vishi

---

### Post by guarin1949 on 2009-07-19
How did you fix this?

---

