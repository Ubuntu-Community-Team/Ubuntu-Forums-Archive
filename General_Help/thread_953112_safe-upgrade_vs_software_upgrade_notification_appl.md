---
title: "safe-upgrade vs software upgrade notification applet"
date: 2008-10-19
forum: General Help
---

### Post by ikki_72 on 2008-10-19
I wonder after I did **sudo aptitude safe-upgrade**, the update notifier still says there's 9 updates and **sudo aptitude upgrade** which aptitude says already obsolete and **install all updates** from the applet could get rid of that. Why?

---

### Post by ghost_ryder35 on 2008-10-19
man pages are your friend
```

man aptitude

       safe-upgrade
           Upgrades installed packages to their most recent version. Installed
           packages will not be removed unless they are unused (see the
           section &#8220;Managing Automatically Installed Packages&#8221; in the aptitude
           reference manual). Packages which are not currently installed may
           be installed to resolve dependencies unless the --no-new-installs
           command-line option is supplied.

           It is sometimes necessary to remove one package in order to upgrade
           another; this command is not able to upgrade packages in such
           situations. Use the full-upgrade command to upgrade as many
           packages as possible.


```

---

### Post by ikki_72 on 2008-10-19
hm..so **full-upgrade** is the way to go in my case. Thanks.

---

