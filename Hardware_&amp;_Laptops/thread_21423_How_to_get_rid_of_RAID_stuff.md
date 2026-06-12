---
title: "How to get rid of RAID stuff?"
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by Shambler on 2005-03-22
When I boot up my system it says "Setting up RAID devices" or something like that. Since I don't have any raid devices, is it safe to remove that (service?)? And if so, how can I do that? I already removed mtab with rcconf.

---

### Post by acascianelli on 2005-03-22
im not completely sure on this but try to remove execute permissions on /etc/rcS.d/S25mdadm-raid

---

### Post by Shambler on 2005-03-22
Sorry for my typo, but i meant i disabled mdam, not mtab...

---

### Post by acascianelli on 2005-03-22
heres another tip i just found...

edit /etc/defaults/mdadm

change "START_DAEMON" and "AUTOSTART" to false.

---

### Post by alastair on 2005-03-22
As well as any /etc/default options, you can remove any startup services (note - just the links) using :

update-rc.d -f <name> remove

See : man update-rc.d

e.g.

update-rc-d -f mdadm remove

Will remove any "S" (start) and "K" (kill/stop) links - so these services do not start up anymore. If you want to start anything afterwards, you can still start via "/etc/init.d/<name> start", or put the links back using "update-rc.d".

---

### Post by Shambler on 2005-03-22
Yes, but isn't that exactly, what the rcconf tool is doing?

---

