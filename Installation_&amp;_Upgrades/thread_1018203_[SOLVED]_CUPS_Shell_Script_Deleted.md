---
title: "[SOLVED] CUPS Shell Script Deleted"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by TunaCanTommy on 2008-12-21
I had some printing problems with a recent update to Intrepid.  As I was trying to fix the issue I purged and reloaded all the CUPS stuff. Now I can't seem to get the CUPS Service to restart . . found out I deleted the CUPS shell script in /etc/init.d. When ever I try to start CUPS I get "Command not found", I looked for the file and it's not there.

Any advice on how to get it back ? ?

---

### Post by cariboo on 2008-12-21
You could try in a terminal:

```
sudo apt-get purge cups
```

and then reinstall cups. The purge options removes all of cups in cluding the configuration files, and once they are removed you should be able to reinstall.

Jim

---

### Post by TunaCanTommy on 2008-12-22
That did it . . . thanks Jim.

---

