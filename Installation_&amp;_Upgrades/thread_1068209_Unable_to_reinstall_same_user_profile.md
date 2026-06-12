---
title: "Unable to reinstall same user profile"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by lazylogic on 2009-02-12
I am trying out Ubuntu 8.10 and had installed /home in a separate partition. 4 users were created.

After many days of messing around, noticed that I've installed/removed to much things and wanted to start all over again as a new installation.

Reinstalled Ubuntu 8.10 but was unable to create the user profiles using the previous user profile settings that were in the /home partition.

Error message :
> 
**Home directory already exist**
Please enter a different home directory path
Remembered that I was able to do the same in Debian :confused:


Where did I do wrong?

---

### Post by lemming465 on 2009-02-14
Run the install specifying that you want to reuse the /home partition without reformatting it, and create a new, temporary admin / first user account with a different name.  You'll have to add back the other 4 users and edit your regular account to have sudo privileges later.

---

### Post by tarpon_bill on 2009-04-24
Could you elaborate on how to add back users? I get the same can't use message and there seems no easy way out.

---

