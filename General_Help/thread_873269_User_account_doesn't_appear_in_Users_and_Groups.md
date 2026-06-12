---
title: "User account doesn't appear in Users and Groups"
date: 2008-07-28
forum: General Help
---

### Post by mdw1982 on 2008-07-28
Hi All,

I've run into a strange situation. After installing Ubuntu 8.04 today and getting everything setup I ran into a few problems.

1. Set up samba connections to network shares being shared from a Samba server running on a CentOS 4.6 box:
- put entries in fstab to mount samba shares on local file system (/mnt). set it up this way so I could create sym-links in my home directory.
- found a few access problems because of the disparity of UID/GID values between the Ubuntu and CentOS systems.
- removed user account with UID of 1000 and recreated user account with UID/GID of 500/48 to match that of the user account on the Samba server. 
- recreated user account on Ubuntu desktop and migrated user data into new user account and chown'd all files for this user. 

The user account works except I can't use sudo on this account and the user account doesn't show up in the User and Groups utility; nor does the group name for the GID 48 (apache).

Since I'm used to the way things are done in RHEL based distros I'm not sure what's going on. I'm still getting the hang of having to use sudo to perform admin tasks, so I'm not sure where to look to correct the problem that is preventing this user account from appearing in the Users and Groups utility.

Any ideas?

Mark

---

### Post by mdw1982 on 2008-07-28
Ok... not necessarily a good thing replying to your own posts, however I figured out what the problem is with this user account. Since the UID is lower than 1000 Ubuntu considers this a system account which is why it wasn't showing up.

Had to install KDE to get it sorted out...

live and learn I s'pose.

---

