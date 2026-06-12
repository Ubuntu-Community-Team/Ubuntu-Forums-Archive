---
title: "What to backup before upgrade?"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by mgbridges on 2009-08-17
I'm getting ready to upgrade my desktop from 7.10 to 8.04. Based  on past experience I plan to do this as a fresh install. What key files/folders should I be backing up to make sure I don't have to rebuild my SAMBA config etc.?

Thanks.

---

### Post by oboedad55 on 2009-08-17
> **mgbridges said:**
> I'm getting ready to upgrade my desktop from 7.10 to 8.04. Based  on past experience I plan to do this as a fresh install. What key files/folders should I be backing up to make sure I don't have to rebuild my SAMBA config etc.?

Thanks.

Can't help with samba, but I'm sure you know to backup your /home directory.

Jon

---

### Post by swerdna on 2009-08-17
> **mgbridges said:**
> I'm getting ready to upgrade my desktop from 7.10 to 8.04. Based  on past experience I plan to do this as a fresh install. What key files/folders should I be backing up to make sure I don't have to rebuild my SAMBA config etc.?

Thanks.

1: smb.conf from /etc/samba/smb.conf 
2: if you're using Usershares as created with the sharing tool in Nautilus, also backup the files in /var/lib/samba/usershares
Probably 2 is unnecessary -- just a thought.
It's no drama to re-create the users in the Samba user database

---

