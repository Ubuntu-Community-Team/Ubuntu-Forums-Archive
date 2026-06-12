---
title: "[SOLVED] Group Permissions"
date: 2008-07-23
forum: General Help
---

### Post by CrusaderAD on 2008-07-23
I'm trying to assign certain privledges to a folder for a certain group. When I click on groups, my new group is not listed. Why?

---

### Post by sisco311 on 2008-07-23
did you log out/log in after the new group was created?

---

### Post by CrusaderAD on 2008-07-23
Yes. I logged in as the new user, but since that user is not the owner, I can't change permissions. When I log back in as the owner, it still doesn't list the group I need.

---

### Post by sisco311 on 2008-07-23
did you add your user to the group?
```
sudo addgroup *username* *groupname*
```

try to change the group from the terminal:
```
chgrp *groupname ./path/to/dir*
```

---

### Post by Darkspark on 2008-07-23
Did you happen to use the chown command? 

chown [OPTION]... [OWNER][:[GROUP]] FILE...

If not, that command might help you. Here is a link to the command.

[http://linux.die.net/man/1/chown](http://linux.die.net/man/1/chown)

---

### Post by CrusaderAD on 2008-07-23
Tried that... no go. The user is in the group. What I want to for this folder to be mapped as a network drive using the new user/pass. I want this new group (to which this user belongs to) to have full access to this folder, but no other.

---

### Post by CrusaderAD on 2008-07-23
Man this was bothering me for a LONG time and the answer was so obvious. When mapping a ubuntu network drive from Windows you need to have a samba user name and password setup for that user. I knew I was forgetting something (Shakes Head). Here's the code to set one up:

sudo smbpasswd -a username 

Once that is setup, you can log into these drives with any user name/password you want.

---

