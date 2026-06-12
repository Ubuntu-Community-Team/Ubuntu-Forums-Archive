---
title: "cd tray eject bux fix workaround solved"
date: 2008-11-04
forum: General Help
---

### Post by sdowney717 on 2008-11-04
here is a fix that people say will work, and i tried it and it DOES WORK fine.
It is now in Intrepid proposed but until they push it out, then you can fix it yourself right now. It is easy to fix.

Open a terminal window
type in sudo gedit /etc/udev/rules.d/60-persistent-storage.rules
Add that one line below the other, all it is is a change from a ! to an =
save it, no reboots needed and it works.

[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/283316](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/283316)

[email]prower2000@hotmail.com[/email] wrote on 2008-11-01: (permalink)

* Modified to include untested patch for cd/dvd tray issue (3.7 KiB, text/plain)

i can confirm this issue exists, brasero is currently (for me at least) impossible due to the speed at which the tray opens and closes itself

i made a one-line fix to /etc/udev/rules.d/60-persistent-storage.rules that seemed to solve the problem without even rebooting the machine, it was mentioned in another thread...look for the following in said file:

# skip unpartitioned removable media devices from drivers which do not send "change" events
ENV{DEVTYPE}=="disk", KERNEL!="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"

just beneath the second line, add the following (make sure to back up your original):

ENV{DEVTYPE}=="disk", KERNEL=="sd*|sr*", ATTR{removable}=="1", GOTO="persistent_storage_end"

(the subtle difference is in the "KERNEL" portion)

i'll attach my "version" of the file in case anyone would like to try it themselves as a temporary workaround:

---

