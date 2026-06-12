---
title: "no root access to system"
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by shams2 on 2006-02-05
hi,
i installed the latest ubuntu, while installaion like other linux distros, i didn't see any prompt for the root password to create one, but ubuntu asked me to add new user and i added  my user name and password and  not the root one, now i can login to my user account but don't have the root privelages, when i want to use other dirctories then home or install any thing  the error is permission denied or root can do that, i tried to login as root and just hit the enter for password,  the error is you must type a pssword, or when i used to do su for the root  from my usr account asking for the root password that is not created  at all, please help me what to do?

---

### Post by dickohead on 2006-02-05
ubuntu utilises "sudo", once you get used to it you'll see how much better it is. But as for the root pasword type this as the current user:

sudo passwd
enter YOUR password
enter root password
enter root password again

and done.

When you dod system admin tasks as your normal user, type in your normal users password to gain access.

---

### Post by aysiu on 2006-02-05
Just create a launcher with this command: ```
gksudo nautilus
``` and enter your own password.

If you're using Kubuntu: ```
kdesu konqueror
``` instead.

**There's no need to log in as root in Ubuntu/Kubuntu** to accomplish root-like tasks.

---

