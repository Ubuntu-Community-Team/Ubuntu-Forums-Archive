---
title: "Lost user name and password and tried everything"
date: 2008-09-18
forum: General Help
---

### Post by bruce48 on 2008-09-18
I have lost my user name and password " Dumb ". I have tried all the ways described to recover. I have typed in rw init=/bin/bash and get the root shell and type in passwd and get " authentication service cannot be retrieved authentication info" I have tried the recovery mode and I type in passwd and get " Give root password for maintenance ". I am at wits end and would love to get back into the os. Need some help nothing is working. I don't even know how to erase it because XP is also loaded. Thanks Bruce

---

### Post by mb_webguy on 2008-09-18
Boot into recovery mode, then type "ls /home".  This will show you the home directories on your system, which will be named the same as the user accounts that own them.  Once you've figured out which one is your user account (which should be easy if you're the only user on the system), type "passwd <username>", where <username> is the name of the account.  This will allow you to change your password.

---

### Post by eskimopie2100 on 2010-01-17
But, I do not remember my user name!  What do I do?  I did reset my password, but still cannot access my computer.

---

### Post by Uncle Spellbinder on 2010-01-17
Maybve this will help. Did a google search for "recover username karmic" and this showed. Hope it helps...

[http://www.ubuntugeek.com/howtorecover-your-username-and-passwordfix-grub-21-error-in-ubuntu.html](http://www.ubuntugeek.com/howtorecover-your-username-and-passwordfix-grub-21-error-in-ubuntu.html)

---

### Post by sisco311 on 2010-01-17
> **eskimopie2100 said:**
> But, I do not remember my user name!  What do I do?  I did reset my password, but still cannot access my computer.

type
```
ls /home
```to list the home directories.

Usually the login name is the same as the name of the home directory.

For details see
[http://psychocats.net/ubuntu/resetpassword]("http://psychocats.net/ubuntu/resetpassword")

---

### Post by Iowan on 2010-01-17
You should be able to use the recovery mode to check users listed in /etc/passwd - if you don't discover the the home directory... more cumbersome, but another option.

---

