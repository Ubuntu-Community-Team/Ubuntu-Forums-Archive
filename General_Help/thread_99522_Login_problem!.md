---
title: "Login problem!"
date: 2005-12-05
forum: General Help
---

### Post by HarlemHenke on 2005-12-05
Why could I don't login as my root user in Kubuotu. Every time I tried to log on to Kubuotu the sign "Root logins are not allowed" comes up! My question is how do I login as a root user?

---

### Post by atoponce on 2005-12-05
Root logins are disabled by default.  In fact, the entire root account is disabled by default in Ubuntu.  You can manage everything you can do with root using your own account by using the 'sudo' command. Why do you need to enable root?

---

### Post by mlomker on 2005-12-05
You can edit a line in /etc/kde3/kdm/kdmrc to change that.  I don't recommend it, though, because logging in as root can change file permissions that your regular user then won't be able to access.  It's much better to use **sudo**.

---

### Post by HarlemHenke on 2005-12-06
[QUOTE=atoponce]Root logins are disabled by default.  In fact, the entire root account is disabled by default in Ubuntu.  You can manage everything you can do with root using your own account by using the 'sudo' command. Why do you need to enable root?[/QUOTE]

Beacurse I need to change some lines in the sources.list

---

### Post by Rinzwind on 2005-12-06
[QUOTE=HarlemHenke]Beacurse I need to change some lines in the sources.list[/QUOTE]


Log in with your normal account and when you are in  the directory where you need to change that file use:
> sudo kwrite sources.list

That's the normal way to do it :)

---

### Post by atoponce on 2005-12-06
Use the 'sudo' command.  There is no reason for activating the root account in Ubuntu.

---

