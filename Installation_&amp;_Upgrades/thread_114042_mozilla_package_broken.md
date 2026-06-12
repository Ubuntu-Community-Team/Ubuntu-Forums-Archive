---
title: "mozilla package broken"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by wfjm on 2006-01-07
Trying to install mozilla gives
```
The following packages have unmet dependencies:
  mozilla: Depends: mozilla-browser (= 2:1.7.12-0ubuntu2) but 2:1.7.12-1ubuntu1 is to be installed
           Depends: mozilla-mailnews (= 2:1.7.12-0ubuntu2) but it is not going to be installed
           Depends: mozilla-psm (= 2:1.7.12-0ubuntu2) but 2:1.7.12-1ubuntu1 is to be installed
E: Broken packages

```

Reason is, that
[INDENT]mozilla meta-package (2:1.7.12-0ubuntu2) depends on 
[INDENT]  mozilla-browser (= 2:1.7.12-0ubuntu2)
  mozilla-mailnews (= 2:1.7.12-0ubuntu2)
  mozilla-psm (= 2:1.7.12-0ubuntu2)
[/INDENT][/INDENT]

while the Breeze distribution offers
[INDENT]  mozilla-browser   2:1.7.12-1ubuntu1
  mozilla-mailnews  2:1.7.12-0ubuntu2
  mozilla-psm       2:1.7.12-1ubuntu1
[/INDENT]

The whole mozilla suite is uninstallable because all the dependencies require equal revision level, but this is not offered. This situation persists since January 2nd, is thus not a transient.

---

### Post by wfjm on 2006-01-28
This is now a reported and confirmed bug, see
   [https://launchpad.net/distros/ubuntu/+source/mozilla/+bug/6387](https://launchpad.net/distros/ubuntu/+source/mozilla/+bug/6387)

---

### Post by towsonu2003 on 2006-01-30
thanks! got this done thanks to you!!

---

### Post by wfjm on 2006-01-31
The issue is resolved, see [https://launchpad.net/malone/bugs/6387](https://launchpad.net/malone/bugs/6387) .

The 'breezy-update' repositories have to be enabled in sources.list. Unfortunately, the provided sources.list file did not contain these lines in a 'ready to be commented out' form.

---

### Post by carcrashnights on 2006-02-24
Thanks for posting about this. I was having this problem, too.

One minor correction, though. You must add the 'breezy-updates' repositories (the 's' was missing on the previous post).

Thanks again for all of your help.

---

