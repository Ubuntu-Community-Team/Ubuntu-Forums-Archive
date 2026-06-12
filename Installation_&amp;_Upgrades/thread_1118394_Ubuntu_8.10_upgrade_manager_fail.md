---
title: "Ubuntu 8.10 upgrade manager fail"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by gedinfo on 2009-04-06
I have not had any problems with upgrades until now.  My system froze while in the middle of an update, and after a reboot, I restart the upgrade manager, and click on Check. 42 updates are downloaded, and then, I get this message:

An error occurred
The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

After typing this in, I get a message stating:
dpkg: requested operation requires superuser privilege

so, I type su
and get asked for the Password.
I typed in my default password, the same one as I use for the update manager and to log in, and it is not what su is expecting.
I do not remember anywhere during the original installation for a superuser password.

How can I find out what my su password is?

Thank you for any help in this matter.

---

### Post by gtccswsv on 2009-04-06
Do you have a root account and the root password?

---

### Post by Partyboi2 on 2009-04-06
Instead of using su use sudo so in a terminal type
```
sudo dpkg --configure -a
```

---

