---
title: "upgraded to 9.04 and installed services are not autostarted"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by emil on 2009-04-24
Hi,

did an upgrade of my home server to 9.04 and now some of my services are not starting at boot time. Samba, fail2ban, avahi etc are some examples. If I manually start them (i.e. sudo /etc/init.d/avahi-daemon start) it works.

Any ideas to what might have happened and how to fix?

rgds

Emil

---

### Post by nv22nv on 2009-04-24
I once had a somewhat similar problem when using the TOR application in combination with pam-mount: When TOR was installed, those services wouldn't start. I figured that TOR was to be started first, and although it worked fine, it must have somehow prevented other services from being started. When I uninstalled TOR, everything worked alright again.

I don't know if this helps, but perhaps you're in a similar situation and some "special" service is responsible for your problem.

---

### Post by steak on 2009-04-24
Something you could look at is the rc scripts. These run at different stages of boot time starting various daemons. Sorry, I don't know much about how they are exactly configured. But a quick search on google or these forums should help you on your way.

---

### Post by emil on 2009-04-26
Thanks for help, 

just as previous posters suggested it was a rouge service (one of my own, a SCREEN session that I always want to start) that misbehaved and caused the other services not to start.

The upgrade to 9.04 has been very smooth besides this.

/E

---

