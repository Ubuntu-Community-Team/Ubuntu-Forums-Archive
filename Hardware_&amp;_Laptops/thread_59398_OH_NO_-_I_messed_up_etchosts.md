---
title: "OH NO - I messed up /etc/hosts"
date: 2005-08-23
forum: Hardware &amp; Laptops
---

### Post by ubuntuthinking on 2005-08-23
OK - I don't know what happened but when I try to logon I get:

"Could not lookup internet address for ubuntu.  This will prevent GNOME from operating correctly.  It may be possible to correct the problem by adding ubuntu to the file /etc/hosts."

I know that my machine name was left as "ubuntu" .  I can use dial up but cannot run networking setup to fix the problem.

Is there a way to "apt-get" my way thru this mess???

---

### Post by ubuntuthinking on 2005-08-23
Found a thread  - recommended this and it worked!

gedit your /etc/hosts

replace with the following (substitute) your machine name:

127.0.0.1 localhost.localdomain localhost <yourhostname>
# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

