---
title: "Selected wrong authentication during update to 8.10"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by gkmayer on 2009-04-03
During the update to 8.10 from Hardy, I forgot that I had attempted to use LDAP authentication and, in fact, didn't think it was authenticating via LDAP.  But, I guess I was wrong because login failed after rebooting.

I started the system in 'maintenance mode' and tried to issue a 'passwd' command.  I got the message:

passwd: Authentication service cannot retrieve authentication info
passwd: password unchanged

I also tried to su to a user account ( su userid ) and got:

su: Authentication failure
(Ignored)

I changed nsswitch.conf from 'compat' to 'files' to no avail.  I really don't know where to go from here.  There is a valid password file in /etc.  Is there any way I can disable whatever is causing this and use the password, shadow and group files?

Any help would be greatly appreciated.

Thanks in advance.

---

