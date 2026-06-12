---
title: "Postfix broken after upgrade to 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by cmulcahy on 2009-10-30
I just upgraded to 9.10.

Unfortunately, my postfix config got broken somehow.  My main.cf file is fine but for some reason, my virtual aliases are not working.  I keep getting "User unknown in virtual alias table".

Frustrating...

/etc/postfix/main.cf
...
mydestination = office, localhost.localdomain, localhost, myowndomain.com
virtual_alias_domains = example.com 
virtual_alias_maps = hash:/etc/postfix/virtual
...


/etc/postfix/virtual
[email]postmaster@example.com[/email]  chris
[email]me@example.com[/email]          chris
[email]abuse@example.com[/email]       chris
@example.com		chris

____________
Notice that I have the wildcard enabled.  I have spam filtering doing a decent job.

If I send to [email]abuse@example.com[/email] I get the "User unknown in virtual alias table".

Nothing I send will get there.  I have done the postmap /etc/postfix/virtual and postfix reload

Any ideas?

Thanks

---

### Post by cmulcahy on 2009-10-30
Removed and resolved.

---

