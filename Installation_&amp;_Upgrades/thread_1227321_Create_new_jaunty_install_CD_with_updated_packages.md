---
title: "Create new jaunty install CD with updated packages"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by bedge on 2009-07-30
I've been playing with the CD modification tools:

[INDENT][http://https://help.ubuntu.com/community/InstallCDCustomization]("https://help.ubuntu.com/community/InstallCDCustomization")[/INDENT]

 and ran into the issue that the packages on the CD are too old for the package dependencies of additional packages I need to add.

Is there a tool to update the install CD pool, indexes, etc to generate a CD that is up to date WRT package updates?

I want to include updates from:

```
jaunty main restricted universe multiverse
jaunty-backports main restricted universe multierse
jaunty-proposed main restricted universe multierse
jaunty-security main restricted universe multivrse
jaunty-updates main restricted universe multivrse

```

If I replaced the existing packages in cd's pool/... tree, what else would have to be updated?

-Bruce

---

### Post by bedge on 2009-07-31
bump.

---

