---
title: "Trying to get wine to work on 7.10"
date: 2008-07-16
forum: General Help
---

### Post by edward fish on 2008-07-16
Trying to install Wine on Ubuntu 7.10

I get this when trying to install wine using

sudo apt-get install wine

(This is after I've done everything they asked for on the Wine website, as far as installing Wines goes)

then this happens:
The following information may help to resolve the situation:

The following packages have unmet dependencies:
wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
Depends: libaudio2 but it is not installable
Depends: libldap-2.4-2 (>= 2.4.7) but it is not installable
Depends: winbind but it is not installable
PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed

Can anyone help me?

---

### Post by Partyboi2 on 2008-07-16
Make sure you have all the repos except source code enabled  under Software Sources

---

### Post by edward fish on 2008-07-16
Kk, all the repos except source code are enabled, and now when I try I get this error.

The following packages have unmet dependencies:
  wine: Depends: libldap-2.4-2 (>= 2.4.7) but it is not installable
        PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.14.5ubuntu16 is to be installed
E: Broken packages

---

### Post by Partyboi2 on 2008-07-16
try
```
sudo apt-get -f install
``` to fix the broken package.
Have you tried to install the package manually from [[COLOR=Blue]winehq[/COLOR]]("http://winehq.org/site/download-deb")

---

### Post by mc4man on 2008-07-16
@ Partyboi2 this is one of those instances of multiple threads
[http://ubuntuforums.org/showthread.php?p=5397268#post5397268](http://ubuntuforums.org/showthread.php?p=5397268#post5397268)

---

