---
title: "Gnome freezes for no reason"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by fredrik_human on 2009-02-12
Hi, i cant seem to find any info on this subject that's related to 8.10 so i go ahead and see if anyone has experienced the same problem. 

On a clean install with 8.10 and nvidia-glx 177 drivers enabled, gnome freezes from time to time and the only thing i can do is to hit ctrl-alt-backslash. This means that all my current work goes down the drain and i have to start all over again. There's no special patterns for this behaviour, it just randomly happens. 

My graphics card is an Nvidia 7950GX2 and according to my xorg.conf file everything seems ok. The pci bus number is correct and it generally works ok until it freezes. I have enabled the "extra" desktop effects and installed ccsm but i don't know if that matters here. 

Anyone who has had this kind of problem? 

Regards

/Fredrik

---

### Post by fredrik_human on 2009-02-12
As i looked in /var/log/messages, i found this error around the time i had the most recent freeze up: 

"bonobo-activation-server (fredrik-7517): could not associate with desktop session: Failed to connect to socket /tmp/dbus-tAK8Bfqzo4: Connection refused"

As i understand it bonobo is something like a process controlling components in gnome so it might have something to do with my problem to but i don't know.

---

