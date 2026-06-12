---
title: "How do I cancel apt-get install?"
date: 2008-10-19
forum: General Help
---

### Post by imolafem on 2008-10-19
I was trying to install the latest version of freenx, but due to the repository missing some of the libraries needed for the dependancy, I cannot go any farther.  However, if I try to use apt-get to install anything else, it thinks its still trying to install the software that I can't install.

How do I 'clear out the cache' or get rid of what apt-get thinks its supposed to try to install so I can get my system back to normal?

Thanks!

---

### Post by spiderbatdad on 2008-10-19
```
sudo apt-get autoclean && sudo apt-get autoremove
```

```
man apt-get
```

---

### Post by imolafem on 2008-10-19
Don't think that did it:

```

amanda@kubuntu804:~/x360MediaServe$ sudo apt-get autoclean && sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  nxagent: Depends: libxcompshad3 but it is not installed

```

---

### Post by CloudFX on 2008-10-19
Try using

```
sudo apt-get freenx --ignore-missing
```

then, once it has installed, uninstall it with

```
sudo apt-get remove freenx
```

Then:

```
sudo apt-get autoclean && sudo apt-get autoremove
```

---

### Post by imolafem on 2008-10-20
Nope, that won't do it either:

```
amanda@kubuntu804:~/x360MediaServe$ sudo apt-get install freenx --ignore-missing
Reading package lists... Done
Building dependency tree
Reading state information... Done
freenx is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  nxagent: Depends: libxcompshad3 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
amanda@kubuntu804:~/x360MediaServe$ sudo apt-get install -f freenx --ignore-missing
Reading package lists... Done
Building dependency tree
Reading state information... Done
freenx is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  nxagent: Depends: libxcompshad3 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
amanda@kubuntu804:~/x360MediaServe$

```

---

### Post by bionnaki on 2008-10-20
what happens if you simply do

sudo apt-get -f install

?

---

### Post by imolafem on 2008-11-02
> **bionnaki said:**
> what happens if you simply do

sudo apt-get -f install

?

What I had to end up doing was force the install on everything, then remove the stuff I didn't really want there.

There seems to be no way to clear installs of things that are 'stuck'.

---

