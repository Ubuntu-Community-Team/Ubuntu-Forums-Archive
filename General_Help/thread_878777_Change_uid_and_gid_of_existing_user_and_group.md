---
title: "Change uid and gid of existing user and group"
date: 2008-08-03
forum: General Help
---

### Post by Chris86 on 2008-08-03
Hi everybody
I'm trying to set up file sharing via NFS. I own two computers both holding the same users an groups but uids and gids differ. Since NFS is based on uids and gids I have to find a solution to  adapt uids and gids on both machines.

My idea was two distribute new uids and gids to affected users and groups and to change owner and group of already existing files using:

```
find / -uid (OLD-UID) -exec chown (NEW-UID) {} \;
find / -gid (OLD-GID) -exec chgrp (NEW-GID) {} \;
```

In particular user and group "mythtv" are affected. I want to share videos using NFS between backend and frontend. 
User and group have been created by the system since I used apt-get to install mythtv.
Is it possible to change uid and gid anyway or do I loose certain features like "update capabilitiy" etc. ?

Maybe a stupid question but I'm realy not sure :confused:

Excuse my bad English I'm not a native speaker 8-[

best regards,
Christian

---

### Post by kidders on 2008-08-04
Hi there,

The only way I can see any problem arising is in cases where a UID/GID you're changing follows a convention of some sort. For example, users called www-data very often have UID 33. It's conceivable that software packages might make assumptions that could break things if you were to change www-data's UID.

This doesn't apply to your situation, since your mythtv users have two different UIDs/GIDs. I think your plan should work fine. :-)

To avoid odd behaviour, remember that you shouldn't change anything until all mythtv-related processes are stopped. The output of **ps --no-headers -u mythtv** and **sudo lsof -u mythtv** should both be empty.

---

### Post by Chris86 on 2008-09-15
Hi,
excuse my very late reply. Everything worked as expected. \\:D/

best,
Christian

---

