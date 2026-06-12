---
title: "Multiple users show in &quot;w&quot; and &quot;uptime&quot; when there is only one logged in.."
date: 2008-11-18
forum: General Help
---

### Post by EcKstasy on 2008-11-18
Hi, I've been having trouble from my Ubuntu (hardy heron) box for a few days now, When I check "uptime" and "who" it shows there is 5 users logged in when there is only 1.. here is the output I get.

```
 eckstasy@EU:~$ who
eckstasy pts/0        2008-11-19 01:01 (thedatabase.home)

```

and for uptime...
```

eckstasy@EU:~$ uptime
 01:02:47 up 16 days, 23:48,  5 users,  load average: 0.08, 0.03, 0.00
```

Does anyone know what could be the cause of this?
thanks.

---

### Post by EcKstasy on 2008-11-18
Weird.. My phpsysinfo also shows there is only one user logged in also.

[http://www.escriptirc.com/system/](http://www.escriptirc.com/system/)

---

### Post by EcKstasy on 2008-11-19
anyone?

---

### Post by EcKstasy on 2008-11-19
Nevermind.. I managed to fix my problem using:

```
# Reset /var/log/utmp settings on the fly:
/bin/rm -f /var/run/utmp

# Create a fresh utmp file:
touch /var/run/utmp
chown root:utmp /var/run/utmp
chmod 664 /var/run/utmp

```

---

