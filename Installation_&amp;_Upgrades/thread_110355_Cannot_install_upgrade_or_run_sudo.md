---
title: "Cannot install upgrade or run sudo"
date: 2005-12-30
forum: Installation &amp; Upgrades
---

### Post by kdvgent on 2005-12-30
I newly installed Ubuntu 5.10 - via the expert mode.

Hence I have a root password and a user password.

When I want to install upgrades (or do any other tasks that need root priviliges), I am asked to enter a password.

Neither the root password or my own password works.

And when I try again, no password is asked anymore but also no action is taken.  I need to restart to try again - but I have no idea what password to use.

What can I do to cure this situation?

SOLVED by re-installation (in non-expert mode)

---

### Post by homegrown on 2005-12-30
why not try to set both root & your user account to the same password for a bit

the passwd command will allow you to change your user password

passwd root --- will allow changing the root password...as long as you know the old one.

---

### Post by kdvgent on 2005-12-30
Both passwords are actually the same - at least as far as I remember.  I am obviously sure about my user password , otherwise I would not be able to log on, and it should surprise me that I would have typed twice something different - instead of the same one as that was my intention.

---

### Post by fordfan753 on 2005-12-30
You're probably not in the sudoers file (/etc/sudoers)

---

### Post by kdvgent on 2005-12-30
Probably, but if this is so, I cannot change it - as I need root privileges to do so.

I took the easy way and re-installed (the non-expert way).  Things work fine now.

Thanks for the suggestions

---

### Post by gbushee on 2006-01-03
Thanks for the scoop on this one.
I had the same problem, but did an su to root to edit /etc/sudoers

I added the following two lines to get my user ID to work:

User_Alias      PARTTIMERS = myuserid
PARTTIMERS ALL = ALL

---

