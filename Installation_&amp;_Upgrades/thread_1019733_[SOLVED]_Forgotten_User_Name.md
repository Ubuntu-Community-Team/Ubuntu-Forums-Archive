---
title: "[SOLVED] Forgotten User Name"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by confusedmatt on 2008-12-23
Hi all,

So in my excitement to play with 8.10 on my brand new and very shiny Samsung NC10 I didn't make a note of the default user name the install program created.

Can anyone advise if there is a standard for this, or anyway to find this?

Otherwise, do I need to uninstall and start again?

Thanks in advance for any help,

Matt

---

### Post by sancho panza on 2008-12-23
There is no default username that is created. You would have created a username and password while running the install program. If you cannot remember it,
you need to backup all your personal files and data and reinstall.

---

### Post by lordadi on 2008-12-23
You do not need to reinstall.

At boot, select recovery mode and when it asks for root password just hit enter unless you have changed it. Then ```
ls /home/
``` If there is just one user, it will come back with the username like /home/me/, in which case "me" (no quote) is your username.


Post back in case of problems.


Lordadi.

---

### Post by albandy on 2008-12-23
You don't need to reinstall.

Select safe mode in grub menu, and when you boot select a root session.
do:
cat /etc/passwd
it will show all user names, maybe the last one is your user name.
then do
passwd username
enter the new password.
type reboot

now you can log in with your user name and password

---

### Post by confusedmatt on 2008-12-23
Many thanks for the quick responses.  

Followed the second set of instructions and they were perfect.  The system had picked up my login from the windows install.

I'm now off to play with my new toy and turn off the logon screen.

Thanks again.

Matt

---

