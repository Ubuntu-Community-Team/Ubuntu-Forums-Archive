---
title: "SSH - Can Only Log In From Localhost."
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by slewrate on 2009-10-15
Hello. I just installed SSH. My routers are properly configured (I used to run Debian where SSH remote logins used to work fine) yet I can only login from from localhost. Any other machine (either on my local network or from work etc.) can't log in. 

My hosts.allow / hosts.deny are empty. My port 22 is open, and SSH server is running.

Any help is appreciated.

---

### Post by amingv on 2009-10-16
Are you able to ping the computer?
It could also be a DNS issue, try to SSH to the IP of the computer instead.
Does it give you an error when it doesn't connect? What does it say?

---

