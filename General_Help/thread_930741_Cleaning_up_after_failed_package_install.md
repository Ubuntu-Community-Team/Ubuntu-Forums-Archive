---
title: "Cleaning up after failed package install"
date: 2008-09-26
forum: General Help
---

### Post by tsudonymn on 2008-09-26
This started when the following package failed to install correctly from synaptic. Since then I've tried many things trying to clean up the mess it made. The package is now installed correctly but this failure still remains. So everytime I install updates it retries this package and of course fails. I've tried un/re-installing the package as well as the following. I'm looking to cleanly remove this and not manually delete entries from the bowels of dpkg if I can avoid it. I've also tried the things suggested in similiar posts which is where the snippet came from. Hope you all can help. Thanks in advance.

```
$ sudo dpkg --configure -a
Setting up hybserv (1.9.2-4) ...
Starting Hybserv 2 IRC Services: hybservinvoke-rc.d: initscript hybserv, action "start" failed.
dpkg: error processing hybserv (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hybserv
```

```
$ dpkg --version
Debian `dpkg' package management program version 1.14.16.6ubuntu1 (i386).

```

---

### Post by Infinite Indefinite on 2008-09-27
Not sure this will help, but did you try:

**sudo apt-get autoremove**

That often cleans things up.

---

### Post by Kevbert on 2008-09-27
In terminal try
```
sudo apt-get install -f
```
to repair broken packages.

---

