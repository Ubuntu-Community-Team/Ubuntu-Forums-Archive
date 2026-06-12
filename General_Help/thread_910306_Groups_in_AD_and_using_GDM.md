---
title: "Groups in AD and using GDM"
date: 2008-09-04
forum: General Help
---

### Post by Causer1984 on 2008-09-04
I am having a problem getting groups to work in GDM and Active Directory over LDAP. 
My setup is as described here:
[https://help.ubuntu.com/community/ActiveDirectoryHowto](https://help.ubuntu.com/community/ActiveDirectoryHowto)

And it seems to work fine. The only problem is that when I log using GDM and issue the command "groups" in a terminal, it only has my primary group. However, the problem is more subtle than I originally thought. Here is a demonstration that outlines the problem (I have graphically logged in as ADuser. and got a root terminal. ADuser has primary group called primary_group and a secondary group called secondary_group.):

```

root@comp:/tmp# touch random_file
root@comp:/tmp# chown :secondary_group random_file
root@comp:/tmp# chmod 660 random_file

ADuser@comp:/tmp$ cat random_file                
cat: random_file: Permission denied

ADuser@comp:/tmp$ su ADuser
ADuser@comp:/tmp$ cat random_file
ADuserC@comp:/tmp$

```

So basically it is only GDM that doesn't pick up all my groups. SSH and SU both pick up all the groups fine, and it works if I change over to KDM-KDE4 (I haven't tried kdm yet.) I have moved /etc/pam.d/kdm-kde4 to /etc/pam.d/gdm to no avail.

Does anyone have any ideas? I'm stumped.:confused:

---

### Post by Causer1984 on 2008-09-10
As a followup (and bump ;) ), using kdm doesn't fix it (ie. kdm-kde4 is the only display manager which shows all groups.) 

Also, if I add my AD user to a local group (like admin), it doesn't pick that up either (except when su or ssh are used.)

I'm at a complete loss as to what's going on. I don't particularly want to use kdm-kde4, but if needs must.....

---

### Post by silverglade00 on 2008-09-10
Have you tried using Likewise? I believe it is in the repos as likewise-open or open-likewise, but I have better luck with the version on the website. [www.likewisesoftware.com](www.likewisesoftware.com)

---

### Post by Causer1984 on 2008-09-10
Thanks Silverglade, but it looks a bit like overkill for what is seemingly a very simple problem. I'll try it out later anyway.

How does LikeWise dish out details? Does it use LDAP, because if it's similar to winbind, then that'd be no good here because there will be some *nix to *nix file sharing (ie. UID preservation.) I can't seem to find a sensible answer on their web pages.

---

### Post by Causer1984 on 2008-09-11
Right, fixed, but I don't know why.

I just removed the line

```

auth       optional   pam_group.so

```

in /etc/pam.d/login.

No idea why it worked, because /etc/security/group.conf, once all the comments are taken out, is a blank file!!

---

