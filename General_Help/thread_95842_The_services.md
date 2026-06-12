---
title: "The services"
date: 2005-11-27
forum: General Help
---

### Post by 3dmaker on 2005-11-27
As I said before Ubuntu eats up my battery on my laptop pretty quickly... So i have an idea on how to try and fix it, yet i have no idea how. I noticed I have a bunch of services running like bluetooth, cups, etc... How do I stop those services? All I want is:

Internet
Apache, PHP, MYSQL

thats it.nothing more. How do I do that?

---

### Post by hw-tph on 2005-11-27
You may want to have a look at the Debian Reference and Policy manuals, especially the parts on [system initialization](http://www.us.debian.org/doc/manuals/reference/ch-tune.en.html#s-init-hints) and [runlevels and init.d scripts](http://www.debian.org/doc/debian-policy/ch-opersys#s-sysvinit). Bookmark the manuals, they are very good for understanding how Debian (and Ubuntu) works. 


H&#229;kan

---

### Post by sapo on 2005-11-27
Are you running breezy?

If you are you can go to the Settings -> Services in the menu and turn them off.

Or just

chmod -x /etc/init.d/servicename

For example.. if you wnat to disable apache, type:

chmod -x /etc/init.d/apache

to stop an already running process use:

/etc/init.d/apache stop

Hope it helps.

---

### Post by Abandon on 2005-11-27
services can be uses very easily with a little help of you' re gui. Do a sudo apt-get install bum and check the [original website]("http://www.marzocca.net/linux/bum.html") for information

---

### Post by metoo on 2005-12-04
That's an old thread, but I doubt that the services will make much of a difference. They are idleing anyhow most of the time.
Check if the CPU power management is enabled and your harddrive spins down if not used.

---

