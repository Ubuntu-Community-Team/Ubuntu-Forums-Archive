---
title: "moving 64bit install to a 32bit system?"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by Jesus-Ninja on 2009-04-08
Hello :)

I'm running 64bit hardy on an AMD powered 64bit laptop. It's running as a websever, but at 2GHz and 2GB of RAM it's overkill, and I need to use the laptop for something else. Which means the web server needs to move onto a different laptop.

My intention was to put the hard disk into the new webserver, and hop that ubuntu sorts itself out with the new hardware it'll find, but of course the new laptop is a 32bit 2.4GHz celeron, so I'm guessing it's not that simple :(

Presumably ubuntu will fall over in a heap on this architecture? What's the easy way to migrate without starting from scratch?

---

### Post by ramjet_1953 on 2009-04-08
You could always backup your /home directory and then do a fresh install on the new machine and copy /home across.

Regards,
Roger ;)

---

### Post by Jesus-Ninja on 2009-04-08
Hmmm, it's not so much the back up of personal files (there aren't any really, as it's just a web server), it's more the config of PHP, MySQL and the LAMP apps I run on there... :(

---

