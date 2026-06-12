---
title: "Installing from the CD"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by amantia on 2006-01-05
I'm quite new to kubuntu and apt-get and I'm stuck now. I want to install some packages from the kubuntu 5.10 CD, but it keeps getting the packages from the net, even if they are available on the CD. As a last resort, I cleaned up the /etc/apt/sources.list and did an apt-cdrom add afterwards, so I ended up with the CD as source only. But now if I want to install fbset for example ("apt-get install fbset") it returns an error that there is no package called fbset (there is one on the CD). Same happens with other not yet installed packages.

Can you tell me how to teach apt-get to first try to install from CD (and to recognize what packages are on the CD)?

---

### Post by welsh_spud on 2006-01-05
In synaptic, under repository, click on the CD button. You can add a CD from there. If that doesn't work i'm stumped.

---

### Post by GA\/1N on 2006-01-08
You could possibly be stumped there,

---

### Post by az on 2006-01-08
[QUOTE=amantia]
Can you tell me how to teach apt-get to first try to install from CD (and to recognize what packages are on the CD)?[/QUOTE]


By default, it will pick packages from the local repositories (cdrom) first.  The only reason it will get the same package from the net is if there is a more recent versionlike and update or security-update version available there.

You may have another package installed that will make it so that apt will not install the old version from the cd.

---

