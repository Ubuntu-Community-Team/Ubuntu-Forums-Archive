---
title: "What just happened to openoffice 3.0 on launchpad?"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by andreasis on 2008-12-07
I've installed several system with the oo3 upgrade from here: [https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)
in the past month, but as I was installing another system today I noticed that the repos were empty.

Can anyone confirm this/offer an alternative solution other than download/compiling from the oo website?

---

### Post by ubuntu27 on 2008-12-07
Canonical and Ubuntu were planning to provide upgrade to OpenOffice.org from version 2 to version 3 **sometime in December**

My guess is that the OpenOffice.org 3's PPA (Personal Package Archive) is offline because it is not needed anymore. 

That means you will be able to upgrade to OO.o 3 without adding additional repository. 

I don't know the precise date, so let's just wait :)

---

### Post by frankleeee on 2008-12-07
The ppa is empty due to some bugs in that version, although I have 003 running on two different computers downloaded from the site, with the only problem being the quick systray leaving after any restart.

---

### Post by andreasis on 2008-12-07
>_<* Thanks guys.  At least I know that I'm not crazy after all... and yes, that quick systray bug is impossible.

---

### Post by andreasis on 2008-12-07
I just noticed something interesting: franklee and ubuntu27, if you have office 3.0 installed right now, can you try running this command on bootup: ```
ooffice -quickstart -nologo -nodefault
```

---

### Post by ubuntu27 on 2008-12-07
> **andreasis said:**
> I just noticed something interesting: franklee and ubuntu27, if you have office 3.0 installed right now, can you try running this command on bootup: ```
ooffice -quickstart -nologo -nodefault
```

I don't have OO.o 3 installed. 
What happens when you remove the logo?

---

