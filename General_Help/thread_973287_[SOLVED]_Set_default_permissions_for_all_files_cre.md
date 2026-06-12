---
title: "[SOLVED] Set default permissions for all files created in a directory"
date: 2008-11-06
forum: General Help
---

### Post by 50words on 2008-11-06
I am using Ubuntu on a NFS network between two computers. One of the computers serves as the file server. I use the file server, and my law clerk uses the workstation.

There is an unprivileged user account on the file server, and the business files are in that user's directory. I log in with my own user account.

I control access to files in that directory by setting group permissions on the various folders (only people in group "administration" have access to admin stuff, while people in group "everybody" have access to other thing).

Users' default group is either "administration" or "everybody."

Umask is set to 002 so that files are created with RW group permissions.

What I want is to control the group of newly-created files. For example, if a member of "administration" creates a file in an "everybody" folder, I want that file's group to be "everybody" by default.

Is there any way to do this?

---

### Post by CatKiller on 2008-11-06
I believe it can be done by setting the "setgid" (Set Group ID) flag on the parent folder. I must admit that I haven't got a full handle on Unix permissions, but it's something like that.

---

### Post by geirha on 2008-11-06
Yes, setting the setgid bit on a directory will make all files and folders created inside, get the same group as the directory. 

```
chmod g+s directory
# or in octal
chmod 2775 directory
```

---

### Post by 50words on 2008-11-06
That did it. Thanks!

---

### Post by cprophecy on 2009-01-12
this removed all contents in the directory. not good

---

### Post by 50words on 2009-01-12
> **cprophecy said:**
> this removed all contents in the directory. not good

Not for me. Are you sure you didn't chmod away the ability to view files in the directory?

---

