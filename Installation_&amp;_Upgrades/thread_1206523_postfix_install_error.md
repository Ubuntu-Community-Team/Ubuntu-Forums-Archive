---
title: "postfix install error"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by kukoobash on 2009-07-07
Hi, I am currently trying to setup a mail server using ubuntu. While installing Postfix I have come across this:

```

$ sudo aptitude install postfix
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
 exim4 exim4-config
The following packages will be automatically REMOVED:
 exim4-daemon-light
The following NEW packages will be installed:
 postfix
The following packages will be REMOVED:
 exim4-daemon-light
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 1160kB of archives. After unpacking 1790kB will be used.
The following packages have unmet dependencies:
 exim4-config: Conflicts: postfix but 2.5.1-2ubuntu1.2 is to be installed.
 exim4: Depends: exim4-daemon-light but it is not installable or
                 exim4-daemon-heavy but it is not installable or
                 exim4-daemon-custom which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
exim4
exim4-base
exim4-config

Score is -819

Accept this solution? [Y/n/q/?]

```I have tried reinstalling the broken packages but I still get the same error. I have just installed ubuntu so I can scrape everything and start from the beginning but I was hoping to save the hassle.

Please help! I would really appreciate it.

p.s. I am a total noob when it comes to Linux systems

---

### Post by kukoobash on 2009-07-07
oh never mind, I am totally a noob *shakes head*. Just found out that Exim is another MTA, so I uninstalled it and Postfix installed fine!

sorry for the bother

---

