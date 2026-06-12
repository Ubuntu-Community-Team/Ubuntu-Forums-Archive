---
title: "Kernel seg fault causing application crash"
date: 2008-07-24
forum: General Help
---

### Post by Alisdair Kelly on 2008-07-24
This past weekend I upgraded a Dapper Drake install to Hardy Heron via 
synaptic/update manager. Following the upgrade, every time I open Pan 0.132, Pan crashes. 

The following is a snipped from the system log:
Jul 23 21:56:46 Leonidas kernel: [ 1507.894567] pan[30388]: segfault at 
08e69000 eip b75979bc esp bffa7dbc error 4
Jul 23 21:57:03 Leonidas kernel: [ 1524.609826] pan[30782]: segfault at 
08e09000 eip b75039bc esp bf83c64c error 4

In doing my due diligence, I have found out that these kernel faults are probably poor memory management. Since Pan is the only application that the faults occur in, my first thought was that Pan had been corrupted somehow in the upgrade process. Thus I re-installed Pan, but no real difference: it still crashes.

I could install a newer, non-generic kernel. Current kernel is: 
2.6.24-19-386.
My question is this: should I go that route or is it possible to roll 
back the installation of Hardy and revert to Dapper where I did not have this problem.

---

