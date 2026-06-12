---
title: "svn: Can't connect to host 'localhost': Connection refused"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by smookie on 2009-03-29
I don't have a clue on what's happening since I dont know where to start to get logs with svn. I can checkout my working copy but I can't commit it says: svn: Can't connect to host 'localhost': Connection refused


#cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       smaugzone
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Yes apache is running on port 80
# /etc/init.d/apache2 status
 * Apache is running (pid 2575).

The problem doesn't come from the authentication itself because I clearely get a svn connection refused without trying to authenticate.

ANy help will be reaaaaaaally appreciate :)
Tks

---

