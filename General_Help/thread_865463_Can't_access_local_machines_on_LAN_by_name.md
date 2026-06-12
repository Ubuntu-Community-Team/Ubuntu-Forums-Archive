---
title: "Can't access local machines on LAN by name"
date: 2008-07-20
forum: General Help
---

### Post by airjrdn on 2008-07-20
I can view them in the Windows Network, but double clicking them simply "opens" a blank File Browser window.  Pings by name don't work either.

A CentOS box on the LAN is accessible however, and is seen in the Windows Network.

A share on another XP box seems to work fine though.  All boxes (including Ubuntu) have my same login/pass.

When I try to do an nslookup, I get "server can't find [server name] NXDOMAIN

Everything is setup using a workgroup of WORKGROUP

Samba config shows that Ubuntu is using WORKGROUP as well.

---

### Post by airjrdn on 2008-07-20
Answer found [here]("http://ubuntuforums.org/showthread.php?t=88206")

sudo gedit /etc/nsswitch.conf

add wins to the hosts line

save it

run - sudo apt-get install winbind

Now it'll work

---

