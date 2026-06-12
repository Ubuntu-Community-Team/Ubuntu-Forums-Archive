---
title: "problems installing, well anything"
date: 2008-09-07
forum: General Help
---

### Post by phantom1976 on 2008-09-07
Hi all
 New to Linux here and I have just done a tone of updates to Ubuntu SInce doing these updates I noticed that my add/remove programs is gone and when I try to install anything like flash through the terminal. Or in fact download any updates via the update checked I get this error.. Any ideas?

Thanks

---

### Post by ryanhaigh on 2008-09-07
Are you able to run other sudo commands, did you make any other changes other than the upgrades.

---

### Post by drs305 on 2008-09-07
A few questions to start the troubleshooting (commands in double quotes):

Can you currently use sudo to perform other tasks such as "sudo blkid"?
Are you the first user of the machine (uid=1000)?  "id"
Are you listed in the admin group? "groups"
If you run the following command, does the result look like this with nothing added to your computer's name (e.g. mycomputer, not mycomputer.firefox)?
```

cat /etc/hosts | grep 127

```
```

~: cat /etc/hosts | grep 127
127.0.0.1 localhost
127.0.1.1 yourcomputername

```

Have you tried rebooting?

---

