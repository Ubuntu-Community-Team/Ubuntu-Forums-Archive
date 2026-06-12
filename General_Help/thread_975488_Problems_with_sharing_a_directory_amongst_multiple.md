---
title: "Problems with sharing a directory amongst multiple users (permissions are preserved)"
date: 2008-11-08
forum: General Help
---

### Post by Brucevdk on 2008-11-08
[SIZE="4"]**The problem**[/SIZE]
The most problematic issue I've encountered in trying to make a locally shared directory is that copying files/directories into the shared directory will preserve the existing permissions, both using standard UGO permissions and POSIX ACLs. Manually or even using a cronjob to correct the permissions is obviously not a solution. Also note that I cannot tell the end-user to copy without preserving permissions, I don't have that much control over them.

If somebody were able to present a solution for this issue I'd be satisfied.

I'll summarize several methods which one can use to create a shared directory.

[SIZE="4"]**Common methods for sharing directories**[/SIZE]

[SIZE="2"]**Using standard UGO permissions**[/SIZE]

[LIST]
[*] Set a default umask of 002 in /etc/login.defs (i.e. umask u=rwx,g=rwx,o=rx
[*] Add users to a shared group
[*] Create a directory
[*] Change the group of the directory to the shared group 
[*] chmod g+s the directory (the setgid bit, the group will be inherited for any created directory/file inside the directory)
[/LIST]

However this method is a little bit too inflexible for certain scenarios.

[SIZE="2"]**Using POSIX ACLs**[/SIZE]
For a more extensive discussion, see the following posts: [HOWTO: Local shared folder](http://ubuntuforums.org/showthread.php?t=197839) and [Re: Permissions on a shared directory](http://ubuntuforums.org/showpost.php?p=832721&postcount=9).

[LIST]
[*] Create a directory
[*] Change the ACLs and default ACLs to allow a shared group (in this case foo) read/write access
[LIST]
[*] setfacl -m g:foo:rwx && setfacl -dm g:foo:rwx
[/LIST]
[/LIST]

The default ACL will take care of the permissions.

[SIZE="4"]**References**[/SIZE]

[SIZE="2"]**General references**[/SIZE]
Here are some links that should give you some more insight into the topic.

[LIST]
[*] [Eiciel 0.8 - Users guide](http://rofi.roger-ferrer.org/eiciel/doc/) (describes POSIX ACLs versus UGO permissions)
[*] [Debian mailing list, Re: Umask 002 policy](http://lists.debian.org/debian-user/2004/12/msg03223.html)
[*] [Wikipedia umask](http://en.wikipedia.org/wiki/Umask)
[*] [Launchpad Bug #173267 :Kernel ACL support for NFS/CIFS in 8.04?](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/173267)
[/LIST]

[SIZE="2"]**Ubuntu Forum discussions**[/SIZE]
There are several other threads where the topic of creating a shared directory is discussed. However, the reason I have for creating this thread is to for once and for all solve the issue of files/directories preserving their permissions when being copied into a shared directory (thereby not allowing other users access to these files).

[LIST]
[*] [HOWTO: Local shared folder](http://ubuntuforums.org/showthread.php?t=197839)
[*] [Permissions on a shared directory](http://ubuntuforums.org/showthread.php?p=832721)
[LIST]
[*] [Specific post in this thread talking about this issue](http://ubuntuforums.org/showpost.php?p=3144045&postcount=18) by user [alex.vice.grab](http://ubuntuforums.org/member.php?u=166162)
[/LIST]
[*] [[IDEA] Easy Shared documents between multiple users](http://ubuntuforums.org/showthread.php?t=410065)
[*] [Shared folder permissions (not samba/nfs)](http://ubuntuforums.org/showthread.php?t=249208)
[*] [acl & permissions for sharing folder on same computer](http://ubuntuforums.org/showthread.php?t=924298)
[*] [Shared folder on single machine](http://ubuntuforums.org/showthread.php?t=446611)
[*] [how to share folders](http://ubuntuforums.org/showthread.php?t=50201)
[/LIST]

---

### Post by TuxCrafter on 2008-11-26
bump  up

---

