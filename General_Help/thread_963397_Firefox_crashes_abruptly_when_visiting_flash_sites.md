---
title: "Firefox crashes abruptly when visiting flash sites"
date: 2008-10-30
forum: General Help
---

### Post by Sciamano on 2008-10-30
Hi,
my Firefox 3.0.3 crashes abruptly under Kubuntu Hardy, when visiting some flash sites. Not all flash sites, just a few.
One, for example, is [www.nfl.com](www.nfl.com)

This is the console output:

```
luca@desktop:~$ firefox
CI: {44cc2b80-ac35-4428-9dd1-13c1cf2dfc87}
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault

```

Any suggestion? It's frustrating! 
Thanks

---

### Post by hellion0 on 2008-10-30
What version of Flash are you running? I've heard installing Flash Player version 10 fixes this.

---

### Post by Sciamano on 2008-10-30
I have the *flashplugin-nonfree* package installed.
It's version is 10.0.b218-0ubuntu3

---

### Post by Michl on 2008-10-30
Having the same problem on only one computer a Dell Workstation
220 running nvidia.  It is a recent phenomenon and happens
pretty regularly now.  I'm assuming it is the flashplayer
and nvidia accelerator interaction.

---

### Post by Sciamano on 2008-10-30
I have an NVidia card too.
I've now uninstalled the *flashplugin-nonfree* package, and installed the *adobe-flashplugin* package instead.
No crashes for now, but it's only been running for less than an hour...

---

### Post by Sciamano on 2008-10-31
So far so good. No more crashes.

---

