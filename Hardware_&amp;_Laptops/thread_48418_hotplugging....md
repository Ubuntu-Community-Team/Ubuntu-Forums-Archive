---
title: "hotplugging..."
date: 2005-07-12
forum: Hardware &amp; Laptops
---

### Post by roots on 2005-07-12
hi there...

a little question concerning the hotplug subsystem...

as i understand, the hotplug subsystem is launched by the system on boot. what i would like to know is, who or what actually launches the hotplug script? 

i would like to modify the arguments provided to hotplug to prevent some unnecessary stuff (scsi, pcmcia...) from being started or searched...


thanks in advance,
cheeers!
.roots

---

### Post by varunus on 2005-07-12
You can add modules to /etc/hotplug/blacklist using a text editor.  This will stop hotplug from loading them.

---

### Post by roots on 2005-07-12
thank you, that's correct... but from my curious point of view i'd rather like to know what modules it is trying to load and...as is wrote in my first post, who is telling it to do so...

cheeers,
.roots

---

### Post by az on 2005-07-12
That is a good question.

Hotplug has an entry in the /etc/init.d directory.  So if a runlevel has a symlink to hotplug, it gets run by init when you boot.

Most packages have documentation in /usr/share/doc:

Ex:
usr/share/doc/hotplug

---

