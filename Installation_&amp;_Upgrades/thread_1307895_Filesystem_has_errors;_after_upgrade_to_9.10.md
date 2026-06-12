---
title: "Filesystem has errors; after upgrade to 9.10"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by trayzz on 2009-10-31
I upgraded today to Karmic Koala 9.10 using the update manager. After rebooting I couldn't access ubuntu anymore. Somehow, the filesystem check failed.

This is the error message I receive:
---

Mountall: canceled
/dev/sda8: e2fsck canceled

... . ... . Filesystem has errors .. . ... .

mountall: fsck/home (1035) terminated with status 36
mountall: filesystem has errors /home


---

I had filesystem errors before upgrading already, saying something like filesystem error after 41%. Guess I should have paid attention to it earlier..

Is there anyone who can help me fix this problem, without having to reinstall?

---

### Post by trayzz on 2009-10-31
solved it myself.

basically, to fix filesystem errors manually type fsck and follow instructions. worked for me, though i lost some few files.

---

