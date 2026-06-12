---
title: "Is ACL's not working in 8.04LTS Server?"
date: 2008-11-07
forum: General Help
---

### Post by WhiteShepherd on 2008-11-07
Ok here is where I am. I am trying to use "default" ACL's to override default umask giving Apache vhost users+myuser(a maintaince user) member access to their own folders but not other members folders. I formatted a partition /wwwpages with EXT3.  I edited fstab adding the 'acl' and remounted.  I issued the command:  setfacl -R -m -d u::rwx,g::x,o::x,u:myuser:rwx /wwwpages

This command sets the ACL's on everything and below to:

user::rwx
group::--x
other::--x
default:user::rwx
default:user:myuser:rwx
default:group::--x
default:mask::rwx
default:other::--x

However when I open a terminal and su username when I make a folder or directory it's ACL's are created ls -al shows:

drwxrws--x+ 2 webuser webuser 4096 2008-11-07 12:11 .

Though getfacl shows:

user::rwx
user:myuser:rwx
group::--x
mask::rwx
other::--x
default:user::rwx
default:user:myuser:rwx
default:group::--x
default:mask::rwx
default:other::--x


Is this correct?  LS shows group as having read write?  Plus user "myuser" acts as if it only has "x" permission in all folders under /wwwpages.  He can navigate but cannot see nor edit any files.  I thought acl user:myuser:wrx would give full access?

Thanks for any help.

---

