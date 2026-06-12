---
title: "[SOLVED] running pcmanfm kills x"
date: 2008-08-25
forum: General Help
---

### Post by markp1989 on 2008-08-25
using a light weight openbox setup. every time i run pcmanfm. X gets killed. 

any fix? 

thanks markp1989

---

### Post by eriqjaffe on 2008-08-26
What version of PCManFM are you running?

---

### Post by markp1989 on 2008-08-26
i installed it yesterday using apt, so it should be the new est version,  i dont know the specific number thou

---

### Post by eriqjaffe on 2008-08-26
Looking at the repos, Hardy has 0.3.2.2 and Hardy-Backports has 0.4.3, neither of which are quite current.

There's a PPA repository that has the current version (0.5.0), just add the following to your /etc/apt/sources.list:

```
deb http://ppa.launchpad.net/lxde/ubuntu hardy main
deb-src http://ppa.launchpad.net/lxde/ubuntu hardy main
```

...then just do a sudo apt get update && sudo apt-get upgrade and that should install 0.5.0.

That being said, I haven't seen the problem, however.

---

### Post by markp1989 on 2008-08-26
thankyou, that sorted it out

---

