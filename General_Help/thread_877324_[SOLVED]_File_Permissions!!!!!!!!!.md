---
title: "[SOLVED] File Permissions!!!!!!!!!"
date: 2008-08-01
forum: General Help
---

### Post by CrusaderAD on 2008-08-01
Okay, let me lay this one out here. We have a Ubuntu server setup with two users in Samba. One user logs in and maps the network drive. Both users have read/write privileges. This user uploads files. The second user logs in and attempts to edit the files, but can't, because he's not the "owner". How do we configure it so that both users can edit? We essentially want one user to be the "admin" and the next user to be just a user.

---

### Post by CrusaderAD on 2008-08-01
I think I got it. Open terminal and run > sudo nautilus then you can edit perimissions.

---

### Post by CrusaderAD on 2008-08-01
Can a user belong to more than one group? Cause the files we want to edit belong to one group. We want another group to be able to edit anything. I did assign this admin user to both groups, but he cannot edit the files.

---

### Post by Diabolis on 2008-08-01
Yes, a user can belong to multiple groups.

The commands that you want to learn are **chmod**, **chown** and **ls**.

With ls you can see the permissions and ownership of files.
Example:
```

ls -l files/
-rw-r--r--  1 gaston gaston     1315 2008-07-20 13:11 ifconfig
-rw-r--r--  1 gaston gaston      481 2008-07-20 13:12 iwconfig
```

as you can see those files belong to the user "gaston" and the group "gaston".
If they had 777 permissions they would look like this: **-rwxrwxrwx**


It is actually pretty easy, just look at the help of each command.
```

chown --help
chmod --help
```

I think that you can figure it out now.

[Managing linux accounts]("http://www.cyberarmy.net/library/article/70")

---

### Post by CrusaderAD on 2008-08-01
But can a user belong to more than one group? We want this admin user to be able to edit this stuff.

---

### Post by Diabolis on 2008-08-01
yes

> 6- Groups:

Each user belongs to a group. Every user in a group can have access to certain tools, programs, etc... and one user can belong to multiple groups, but this user can only log with one GID at a time.

---

### Post by ad_267 on 2008-08-01
To add a user to a group:

adduser user_name group

To see what groups a user is in:

groups username

---

### Post by CrusaderAD on 2008-08-01
> **Diabolis said:**
> yes

One GID at a time? How do you check to see which one you are using? How do you change?

---

### Post by Diabolis on 2008-08-01
As posted above, read: [Managing Linux Accounts]("http://www.cyberarmy.net/library/article/70")

It explains GID too.

---

### Post by howlingmadhowie on 2008-08-01
to check your default group: 
groups

(the first entry is your default group)
to change your default group:
newgrp name_of_different_group

this will start a subshell in which you have a different gid. you can check this by entering
groups

---

### Post by CrusaderAD on 2008-08-02
there's an admin group... can this one edit all files regardless of the owner/group?

---

### Post by ad_267 on 2008-08-02
The admin group can use sudo to gain root permissions and then edit anything. They can't edit anything without using sudo.

---

### Post by CrusaderAD on 2008-08-04
I see you can belong to more than one group, but can you use both at the same time? How do they do it with web development? When you ftp files up and what not, if they are not a part of the group that created the files, they cannot replace them.

---

