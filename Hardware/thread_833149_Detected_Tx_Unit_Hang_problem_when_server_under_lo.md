---
title: "Detected Tx Unit Hang problem when server under load"
date: 2008-06-18
forum: Hardware
---

### Post by Pro_D on 2008-06-18
I wonder if anyone can offer advice on this issue.

When I place the system under any kind of load such as transferring files to/from it, but not internet browsing (1 megabit connection) I will get a hand full of messages on screen of the below type and finally the network will simply hang up - all communications on that device fail.

e1000: eth0: e1000_clean_tx_irq: Detected Tx Unit Hang

eth0 is a Intel Corporation PRO/1000 GT Desktop Adapter
OS is Ubuntu Server 8.04 LTS 32 bit on an amd 64 bit processor
2 gigs ram.
That card is connected to a gigabit switch.
The card was purchased just recently.

The information I have come across so far does not seem applicable such as intel's known issues section on the following page:
[http://e1000.sourceforge.net/doku.php?id=known_issues&DokuWiki=ef08304acd3dddfa9f29d844a9b38ac3](http://e1000.sourceforge.net/doku.php?id=known_issues&DokuWiki=ef08304acd3dddfa9f29d844a9b38ac3)

Not really sure what I should be looking at as I am still pretty new to linux.  The machines that are connecting to this system are all windows xp machines but I will be adding one linux system once I get the server 'done'.

---

### Post by Pro_D on 2008-07-03
Ended up replacing the nic, problem solved.  Went with a non-Intel card since to avoid the possible problems.  It's a Rosewill RC-400 (the non lx version) and so far it has worked fine.  It's not quite as fast as the Intel part I had (subjective comparison) but it's certainly stable.

---

