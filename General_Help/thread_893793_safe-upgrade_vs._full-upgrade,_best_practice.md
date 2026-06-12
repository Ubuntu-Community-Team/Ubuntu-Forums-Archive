---
title: "safe-upgrade vs. full-upgrade, best practice?"
date: 2008-08-18
forum: General Help
---

### Post by IvoLucien on 2008-08-18
Please clue me in, is it the usual best practice to use [FONT="Courier New"]aptitude full-upgrade[/FONT] on a production server when updating for security fixes, or should I just use safe-upgrade? My goal is a stable Hardy Heron web server, with the fewest security dangers practical.

Does one normally add [FONT="Courier New"]-t hardy-security[/FONT] to the command? I do have the (default) ubuntu hardy-security lines uncommented in my /etc/apt/sources.list file (I presume that's what aptitude reads) and I'm not sure what's normal or best for my circumstances.

This is on a limited beta web server, so while I'd prefer to avoid configuration issues, I can tolerate some small danger now. But mainly I'm hoping to understand what would be done by an IT admin in these circumstances. Maybe [FONT="Courier New"]update, safe-upgrade[/FONT], then [FONT="Courier New"]full-upgrade[/FONT]?

Thank you kindly.

---

### Post by IvoLucien on 2008-08-18
Oh, and I'm also researching how best to use cron to keep things up to date automatically, presumably a cron.daily script. Thanks again.

---

### Post by tgalati4 on 2008-08-18
The Linux Mint folks got it right:

Postpone kernel and video/xorg updates.

Only update services in use.  I upgrade my Dapper Drake server once every six months.

You could update daily, but be prepared to fix breakage.

I like to leave production machines running as long as possible.  Make sure your UPS battery is working.

---

### Post by Oldsoldier2003 on 2008-08-18
> **tgalati4 said:**
> 

Only update services in use.  I upgrade my Dapper Drake server once every six months.

**You could update daily, but be prepared to fix breakage.**

/me agrees
I subscribe to the school of thought that once you commission a server the only updates that should be done are security updates. Unless the update to a service adds functionality that is "must have" you're better off leaving it alone.

---

### Post by jkohler2 on 2009-06-19
There was a command line upgrade that began apt-get...
and permitted  only upgrading packages that are proven.
Can anyone post it here?

jOHN

---

### Post by wojox on 2009-06-19
Try

sudo apt-get update
and then use
sudo apt-get dist-upgrade
Then restart server

Hope that helps

---

### Post by cariboo on 2009-06-19
I personally only use:

```
aptitude safe-upgrade
```

on my server, that way there aren't any surprises if you reboot. I usually let the kernel get upgraded, but don't reboot until I absolutely have to.

---

