---
title: "Moblock not blocking http access"
date: 2008-07-27
forum: General Help
---

### Post by Sopranosmainman on 2008-07-27
Hey guys, i have the latest release of moblock installed on my freshly installed Kubuntu 8.04.

Unfortunately, moblock does not seem to block any http activity. i have checked off the box in mobloquer to block http, but nothing. i have no problem on another machine of mine.

Wondering if anyone else is experiencing this issue, and if it can be fixed.

---

### Post by jre on 2008-07-28
In the new versions I added "debconf" support, i.e. some configuration questions during package installation/update. One of these questions defaults to whitelist port 80 (http) and 443 (https). I guess that you accepted this default.
Now, indeed there seems to be a bug in mobloquer: mobloquer correctly reads the configfile with WHITE_TCP_OUT="80 443" and therefore shows "http" and "https" as whitelisted. But unchecking these boxes doesn't change the config file. See the debug messages that you get when you start mobloquer from the command line:
```

** Debug: Could not remove value "http" from "WHITE_TCP_OUT" as that value does not exist 
** Debug: Executing command "/usr/bin/gksu" ("cp", "/tmp/temp_moblock.conf", "/etc/default/moblock") ... 
** Debug: Command execution finished.
```

So until this is fixed in mobloquer you have to do it manually. Either do a "dpkg-reconfigure moblock" or edit /etc/moblock/moblock.conf and remove 80 and 443.

I'll contact the mobloquer developer about this issue.
Greets
jre

---

### Post by Sopranosmainman on 2008-07-28
thank you, that worked sir!

---

