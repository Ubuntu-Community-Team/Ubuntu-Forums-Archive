---
title: "File not found during package install"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by aajax on 2009-10-10
On Ubuntu Server (Hardy) I tried to install the Wordpress package.  Aptitude seemed to do the install process as expected but came to a point where the following messages were displayed:

- http://us.archive.ubuntu.com[/url] hardy-updates/main php5-gd 5.2.4-2ubuntu5.6 [ERROR]

- http://security.ubuntu.com[/url] hardy-security/main php5-gd 5.2.4-2ubuntu5.6 [ERROR]

indicating that the files could not be found (i.e., http 404 also reported).

I'm a bit of a novice when it comes to package management with APT/Aptitude and could use some suggestion about how to deal with such a problem.

---

### Post by aajax on 2009-10-10
A little dart throwing seems to have done some good.

I basically updated the package list and upgraded the packages presently installed.  Subsequently, the Wordpress package installed without error.

---

