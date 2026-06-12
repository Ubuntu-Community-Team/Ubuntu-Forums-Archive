---
title: "how to import home backup to a new install"
date: 2008-07-16
forum: General Help
---

### Post by walter_j on 2008-07-16
I backed up my home directory using rsync, then i repartitioned, putting home in a separate partition. I reinstalled ubuntu, and restored the home partition, but i get a message like "need 644 rights to home directory". I tried
chmod -R 0644 /home/walter

but i get an error message on one of the hidden files. Is there a way to easily change the permissions on my backup home directory so that i can access it?

the clean install fixed some nvidia problems,

Thanks

Walter

---

### Post by timcredible on 2008-07-16
the UID on the backup and the new system need to match.  it doesn't matter what the username is, just what the UID is.  when you do ```
 ls -a
``` on the backup, does it show the owner as you, or a number?  if it's a number, then you need to make the UIDs match.  best solution is just change the owner of the old stuff ```
chown -R 
```

---

### Post by walter_j on 2008-07-19
This worked great! thanks

I created partitions for fedora, bsd, and mandriva or pclinux too, so i'm off and running.

---

