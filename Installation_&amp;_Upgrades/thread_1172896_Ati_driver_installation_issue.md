---
title: "Ati driver installation issue"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by danutzmilea on 2009-05-29
Hi! I installed Xubuntu 9.04 a couple of days ago, installed and configured everything i needed except my ATI drivers. So today i downloaded the ATI driver installer from their website, ran the terminal, "sudo su"-ed it, then "sh ./ati-driver-installer-9-3-x86.x86_64.run", then waited for the damn program to unpack and guess what! I got his error message:

```
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.Qowtzw"
```

I'm rather new to Linux, so bare with me. Can anyone help?

---

### Post by Mark Phelps on 2009-05-29
Don't know that particular problem, but Catalyst 9.3 won't run on 9.04.  You need Catalyst 9.4 or newer.  And, if you don't have one of the new "HD" ATI chips or cards, Catalyst 9.4 or newer won't install.

So, basically, unless you have one of the new HD cards or chips, you can't install a Catalyst driver in 9.04.

---

