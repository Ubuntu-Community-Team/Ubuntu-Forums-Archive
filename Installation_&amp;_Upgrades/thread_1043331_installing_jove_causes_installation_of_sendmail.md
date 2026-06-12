---
title: "installing jove causes installation of sendmail"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by wfjm on 2009-01-18
On a freshly installed 8.10 32bit I've tried to install the 
jove package with apt-get install. I get
> [FONT="Courier New"]The following extra packages will be installed:
  m4 procmail sendmail sendmail-base sendmail-bin sendmail-cf sensible-mda
Suggested packages:
  rmail sendmail-doc logcheck resolvconf sasl2-bin
Recommended packages:
  postfix mail-transport-agent fetchmail
[/FONT]

so the installation of an editor causes the installation of an MTA :(.
Looking with synaptic into the dependencies of jove I get
> [FONT="Courier New"]Depends: debconf | debconf-2.0
Depends: libc6
Depends: libncurses5
Recommends: sendmail | mail-transport-agent
[/FONT]

So the dependencies of jove look ok, sendmail is just recommended.

If anybody has an idea why a 'recommended' in the dependency list
is converted into a hard depend ?

Any help/hint highly welcome.

---

