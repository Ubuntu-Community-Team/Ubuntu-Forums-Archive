---
title: "Jaunty Minimum Install Segmentation Fault"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by tallbloke on 2009-06-08
Ok, trying to install jaunty (9.04) on a really old compaq that runs windows 95. Machine has network card and is connected to my router, 48MB RAM, 2GB disc, 166mz

Burnt a minimal install CD (on another pc).

CD in drive and switch on. At boot prompt type "cli"

Do the setup bits for keyboard and whatnot. Things seem to be happening.

After a while I start to see messages of "segmentation fault" and also "Killed"

So I've powered off.

Any help/solutions/suggestions most welcome.

---

### Post by ranch hand on 2009-06-20
Interesting, I have this same problem on Jaunty-64.

Restarted in ricovery and ran fs test.  Rebooted to the same stuff again.

I understand that this could be connected somehow to the ATI driver.  I am not using the proprietory driver because it does't support my card.

---

### Post by ranch hand on 2009-06-20
There is an easy fix for this.

I strongly encourage anyone using this to run a search on this command string before using it. any command with "rm" in it should be used with the knowledge that it will not destroy your system. The cold war term "Trust but Verify" should be followed.

That said

```

sudo rm /var/cache/apt/*.bin

```
should have a curative instant result.

---

