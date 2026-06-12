---
title: "Upgrade to 9.04 from 8.10 via CLI"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by Nopposan on 2009-07-20
Hello there.  I'd like to upgrade.  'Been postponing it for awhile though.  In the meantime, somehow my Update Manager no longer lists the "New distribution available." button.  So, please remind me how to upgrade via the command-line interface.

Thank you.

---

### Post by Nopposan on 2009-07-20
Uh-oh.  'Looks like I'm not even running Ubuntu anymore?

```
$ cat /etc/*release
DISTRIB_DESCRIPTION="DebianEdu/Skolelinux (terra)"
```

O.K., now I remember installing some packages that were meant to be for Edubuntu; that was so that this youngster would have some educational games to play while we were babysitting him.  I didn't know I actually changed my whole distro though.  Whoa.  What's up?

Thanks again.

---

### Post by slakkie on 2009-07-21
what does lsb_release -a tell you?

---

### Post by Nopposan on 2009-07-23
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Debian
Description:	DebianEdu/Skolelinux (terra)
Release:	testing/unstable
Codename:	n/a

```

---

