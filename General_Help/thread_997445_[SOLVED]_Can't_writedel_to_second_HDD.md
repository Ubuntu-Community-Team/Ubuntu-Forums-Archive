---
title: "[SOLVED] Can't write/del to second HDD"
date: 2008-11-29
forum: General Help
---

### Post by PoopyTheJ on 2008-11-29
Ok, so I formatted a second HDD using gparted as ext3 and now I can't do anything with the files already on there, copy/rn/del nor write to the drive without doing it as sudo. What's the deal and how do I fix it so I can write/modify/delete to it as a regular old user?

---

### Post by drs305 on 2008-11-29
If you want to own them:
```

sudo chown -R yourusername: /path.to.mountpoint
chmod -R 700 /path.to.mountpoint

```

---

### Post by drs305 on 2008-11-29
If you want to own them (note the -R switch will do this to all files/subfolders) :
```

sudo chown -R yourusername: /path.to.mountpoint
chmod -R 700 /path.to.mountpoint

```

---

### Post by PoopyTheJ on 2008-11-29
Thank you, is there a way to make it writable for all users?

---

### Post by drs305 on 2008-11-29
> **PoopyTheJ said:**
> Thank you, is there a way to make it writable for all users?

chmod 777 in the above command will give rwx access to everyone. 

Another option would be to create a new group, change the ownership to "username:newgroup", and then giving members of the group write permissions with "chmod -R 770 /path.to.mountpoint.

---

