---
title: "Hal won't start after upgrade"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by lftl on 2009-04-24
Just upgraded to Jaunty from intrepid. Now when I boot the mouse and keyboard won't work. After logging in from another machine and restarting hal everything works fine. 

Hal complains at startup: "Can't start hardware abstraction layer -- please ensure dbus is running"

Sure enough, dbus sends its startup message about five lines after hal starts. Everything appears to be in order in /etc/rc.*. Hal is S24 and dbus is S12, concurrency is set to none in /etc/init.d/rc.

Any thoughts?

---

