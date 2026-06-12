---
title: "find service status"
date: 2008-10-15
forum: General Help
---

### Post by pdtpatrick on 2008-10-15
I recently switched from fedora to ubuntu just because I want to see what all the hype is about although i gotta say, the development is growing fast! 

Anyway in fedora you can run /sbin/service <servicename> {start|stop|restart|status} 

However in ubuntu .. you only have start, stop, restart and something else.. where is the status or how can you check if a service in running? Besides looking at: 

ps -eg | grep <servicename>

---

### Post by Rocket2DMn on 2008-10-15
Moved to General Help.

You can start services with their init scripts in /etc/init.d, so like
```
sudo /etc/init.d/networking restart
``` is a decent example of restarting networking after making config changes.
I think the package "sysvconfig" provides similar usage to RHEL based distros, a quick google search brought up [http://www.cyberciti.biz/tips/how-to-controlling-access-to-linux-services.html](http://www.cyberciti.biz/tips/how-to-controlling-access-to-linux-services.html)
There is also the "rcconf" and "sysv-rc-conf" packages for helping control services and run levels (note that Debian uses different run levels than RHEL based distros).

---

