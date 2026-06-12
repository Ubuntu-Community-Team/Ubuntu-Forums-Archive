---
title: "Add a domain user to local group?"
date: 2008-08-11
forum: General Help
---

### Post by zaphod777 on 2008-08-11
does anyone know how I can add a domain user to a local group?

---

### Post by gkaragoulis on 2008-12-29
Yup, that's an easy one:

Just manually edit the /etc/group file and add whatever domain users to whatever group you want.  Here's an example:

admin:x:115:user1,user2,DOMAIN+user3,DOMAIN+user4
(NOTE: The winbind separator is '+' in this example...)

That would add DOMAIN+user3 and DOMAIN+user4 to the local 'admin' group, and allow them to administer your system.  Just logout and log back in for these changes to take effect.  Verily I say this works, as I just did this successfully 30 seconds before typing this reply.

---

