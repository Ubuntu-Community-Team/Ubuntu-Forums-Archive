---
title: "Megabytes of update for one variable?"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by drumour on 2009-08-19
looking at the changelog for today's 33 meg kernel update there appears to be one minor variable change - quote from changelog:

  * Make sock_sendpage() use kernel_sendpage()
    - CVE-2009-2692


That is 33mb in total according to update manager, 23mb for the kernel itself - am i missing something - seems like a lot of megs for a lot of people for a variable thats a couple of bytes?

---

### Post by Miguel on 2009-08-19
You're right, it doesn't make much sense. The thing is that Debian-based distros, as far as I know, don't support delta patches (that is, incremental). The consequence is that whenever a change happens, updating the relevant package requires updating the whole package. Furthermore, when this involves a series of interdependent patches, many packages can be updated even when the only change is a small bump in the version number and a slight change in the dependency list.

There are, however, distros that support delta patches. I think both openSUSE and Fedora do, although I'm not sure.

---

### Post by drumour on 2009-08-20
Thanks for the prompt and informative response. I hope that incremental updating is on the agenda - it would certainly be greener and help with the adoption of Ubuntu. This is especially the case with those that have to request dvd/cd's because of download restrictions only to find that on installation the very first thing they are confronted with is megabytes of updates

---

### Post by snowpine on 2009-08-20
Yes, Fedora provides this option through their yum presto plugin (it is not the default for Fedora 11, but is easy to install). Don't worry, a lot of the good stuff in Fedora eventually trickles down to the other distros (including Ubuntu).

---

