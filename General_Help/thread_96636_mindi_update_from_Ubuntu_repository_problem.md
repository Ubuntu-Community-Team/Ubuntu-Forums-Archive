---
title: "mindi update from Ubuntu repository problem"
date: 2005-11-29
forum: General Help
---

### Post by jblaty on 2005-11-29
I have downloaded mondo and mindi Deb packages from [http://www.mondorescue.org](http://www.mondorescue.org) and Universe.  When I start with the Deb packages from the source, and do a dpkg, everything works fine.  However, the red update icon lights up, saying that there are newer packages on Universe.

So, I updated...
1.  mondo - all works fine.
2.  mindi-partimagehack - still no problems.
3.  mindi 1.04-6ubuntu1 - that kicks off the problem below...

Now if, I do a:
```
#mindi --version
```

I get:
```
/usr/sbin/mindi: line 2345: syntax error near unexpected token `|'
/usr/sbin/mindi: line 2345: `    while [ "`echo "$newo" | grep "\.\."`" ] ; do'
```

If I downgrade back to the Deb package install, the problem disappears, and the red update icon reappears.

I do have mindi-kernel also installed.

Anyway, I was wondering if anyone had ideas on how to fix the most current package of mindi.  In the meantime, I'm downgrading it until I can find a permanent fix.

Regards,
Joe

---

### Post by phildu on 2006-02-22
I had the same problem.

Look at: [https://launchpad.net/distros/ubuntu/+source/mindi/+bug/3422](https://launchpad.net/distros/ubuntu/+source/mindi/+bug/3422)

I corrected the line as described:

lacks a reverse tilde on line 2268

it is:
        for fname in `echo "$incoming" ; do

and it should be
        for fname in `echo "$incoming" `; do

---

### Post by jblaty on 2006-02-22
Thanks for the link!  That seems to have temporarily fixed the problem.  Hopefully, the next release of Mindi will include this fix.

Regards,
Joe

---

