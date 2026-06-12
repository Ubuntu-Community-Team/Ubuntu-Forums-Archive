---
title: "another install wants to install irrelevant packages?"
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by JohnDow on 2009-03-15
So trying to install smartmontools next, and it also wants to install irrelevant packages:

[INDENT]# apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light mailx
Suggested packages:
  eximon4 exim4-doc-html exim4-doc-info libmail-spf-query-perl swaks
The following NEW packages will be installed:
  bsd-mailx exim4 exim4-base exim4-config exim4-daemon-light mailx smartmontools
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 2267kB of archives.
After this operation, 4977kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
[/INDENT]

Same first question:  How do I only install the package(s) I want?

Second question: Is this sort of this typical with ubuntu?

Thanks!

---

### Post by boof1988 on 2009-03-15
> **JohnDow said:**
> How do I only install the package(s) I want?

The package *smartmontools* needs certain other libraries etc. (as listed in the link below) to oparate.

For example...  Here's [Ubuntu's smartmontools web-page](http://packages.ubuntu.com/hardy/smartmontools), listing the dependencies (requirements) for *smartmontools* on Ubuntu 8.04.

I believe the "*depends*" packages have to be installed for the requested package to run properly. The "*recommends*" and "*suggests*" packages may not be (are not?) required to use the requested package, but may provide useful functionality.  Hopefully someone else can clarify this further.

> **JohnDow said:**
> Is this sort of this typical with ubuntu?

I believe this is typical.  Will let someone else try to explain this.

---

### Post by lswb on 2009-03-15
Try starting synaptic, then select Settings/Preferences/General and make sure that "Consider recommended packages as depencies" is unchecked. I believe this can also be changed by editing an apt configuration file somewhere but I'm not familiar with that.

Smartmontools will use mailx, if installed, to email notification of problems to an admin/root user. That's why it is a "recommended" or "suggested" package for smartmontools. In ubuntu mailx depends on exim so it wants to drag that along as well.

---

