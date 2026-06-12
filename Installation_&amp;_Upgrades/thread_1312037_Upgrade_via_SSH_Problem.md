---
title: "Upgrade via SSH Problem"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by zzzBrett on 2009-11-02
So I am attempting to upgrade a computer remotely using ssh and the command ```
do-release-upgrade
```

It was all going fine, until i stepped away from the computer half way through the install and it was stuck there asking me a question about whether or not to replace a config file.  I wasn't there for a while, so the ssh connection timed out.  Now I cannot reconnect to the server via the standard ssh port nor to the 'backup' port that it set up before starting the install.

Any suggestions on how to proceed? I can have the computer restarted, but I don't know if that will make things worse.

---

### Post by tomBorgia on 2009-11-03
Against my better judgement I did a remote update to my home server... session timed out and the system is trashed... Reinstall time methinks.

Tom.

---

### Post by zzzBrett on 2009-11-03
That's what I figured... there goes my weekend.

---

