---
title: "Trouble with sudo environments (Grails on Ubuntu Server)"
date: 2008-11-04
forum: General Help
---

### Post by Halfling Rogue on 2008-11-04
**SOLVED:** Logged out and back in again, and set the grails command to alias to 'sudo /usr/share/grails/bin/grails'. Seems to work fine now.



I'm trying to run Grails (grails.org) on Ubuntu Server 8.04, and I'm having a bunch of problems regarding sudo environments. Grails requires JAVA_HOME and GRAILS_HOME environment variables to be set (and I have them included in PATH as well; I set them all directly in /etc/environment) in order for it to work correctly. However, Grails also creates directories when creating apps, and Ubuntu won't let it do that unless it's sudo.

/etc/environment looks like this:
```
PATH="/usr/share/grails/bin:/usr/lib/jvm/java-6-sun:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME="/usr/lib/jvm/java-6-sun"
GRAILS_HOME="/usr/share/grails"
```

Problem is, sudo resets all environment variables. I tried editing sudoers:

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#


Defaults        env_keep = "PATH JAVA_HOME GRAILS_HOME"
```

```

# Cmnd alias specification
Cmnd_Alias ALL_OK = /bin/,/sbin/,/etc/init.d/,/usr/,/usr/bin/,/usr/sbin,/usr/share/grails/
```


But it still isn't working. Sudo can't find the command:

```
/usr/share/grails$ sudo grails create-app test
sudo: grails: command not found
```

And lack of sudo can't build dirs:
```
/usr/share/grails$ grails create-app test

Welcome to Grails 1.0.3 - http://grails.org/
Licensed under Apache Standard License 2.0
Grails home is set to: /usr/share/grails

Base Directory: /usr/share/grails
Note: No plugin scripts found
Running script /usr/share/grails/scripts/CreateApp.groovy
Environment set to development
Directory /usr/share/grails/test/src creation was not successful for an unknown reason
```


Is this fixable? Am I not editing sudoers correctly?

---

### Post by Halfling Rogue on 2008-11-04
Bump.

---

