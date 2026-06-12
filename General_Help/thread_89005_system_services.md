---
title: "system services"
date: 2005-11-11
forum: General Help
---

### Post by alvid on 2005-11-11
While trying to install my canon i560 printer i noticed in system services that cupsys was not running and a lot of other jobs that are supposed to run at boot was not running. Tried to manual start and restart in the services panel and also via the terminal noworkee. How do I get the services to start? Help i am a new old guy.

---

### Post by spizkapa on 2005-11-11
You need to find out why the services are not running. To see what's actually being run do:

sudo apt-get install rcconf

Then, in a terminal: 

sudo rcconf

will give you a list of services that are running and others for whom there are scripts on your system but they are not running. New things that you download from synaptic (e.g. apache) automatically add scripts for starting, stopping, restarting in eth right places (/etc/init.d) and make links accross to /etc/rcX.d so that these start.

You may want to do:
man update-rc.d

and read the information there. It's a lot, these scripts go back to the Debian philosophy but it may be worth your time.

HTH

---

### Post by alvid on 2005-11-11
HTH,
Thanks i will try...

---

### Post by mlomker on 2005-11-11
The **bum** package is a nice graphical tool for managing the scripts.

---

