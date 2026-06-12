---
title: "blocking sites via hosts file"
date: 2008-10-16
forum: General Help
---

### Post by robfindlay on 2008-10-16
Here is a copy of my host file

/etc/hosts
***************
127.0.0.1       localhost
127.0.1.1       slag-desktop

0.0.0.0       [www.asstr.org](www.asstr.org)



# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
********************


The asstr.org is the one I want to block but the above doesn't seem to work.

Can anyone offer any advice?

---

### Post by aysiu on 2008-10-16
Maybe try it without the *www.* in front?

---

