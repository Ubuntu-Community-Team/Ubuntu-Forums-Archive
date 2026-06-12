---
title: "Where did ifconfig go in BusyBox w/ intrepid?"
date: 2009-01-30
forum: Installation &amp; Upgrades
---

### Post by howwhi on 2009-01-30
Greetings all,

I really did search the forum first before asking such a trivial question.  My DSL service is PPPoE and I have to set my MTU to 1492.  Been there, done that, been able to install dapper to hardy by switching to second terminal (alt-F2) after network is configured in BusyBox installer (particularly in the server or alternate desktop installs).

Yesterday, I was mid firefight with a 3ware 9650SE raid controller and thought I'd try intrepid server in place of hardy LTS.  At the pause for user name, I switched to tty02 and ??huh??, what do you mean command ifconfig not found in (some directory I forget just now)?  I know the server install disk is getting crowded (used to fit on a 650MB).  Could somebody point me to a URL or forum post that discusses the missing ifconfig command?

Plan B is upgrading my personal repository with intrepid but that takes longer than running ifconfig...

---

### Post by taurus on 2009-01-30
Maybe /sbin is not in your path because ifconfig is in /sbin.  What happens if you run it with a full path?

```
/sbin/ifconfig
```

---

### Post by howwhi on 2009-01-30
Thank you for the response.  "My path" would be the default for the BusyBox terminal :).  Thank you for pointing out where the ifconfig binary hangs out.  Don't have the chance just now to try this out.  Wanted to point out the change in functionality if the change was not intended.

---

