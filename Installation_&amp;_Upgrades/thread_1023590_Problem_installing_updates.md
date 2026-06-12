---
title: "Problem installing updates"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by varunbhatbm on 2008-12-28
Hi,
I get the following error message when I try to install new updates..


Failed to fetch [http://ppa.launchpad.net/rharding/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://ppa.launchpad.net/rharding/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/rharding/ubuntu/dists/intrepid/universe/source/Sources.gz](http://ppa.launchpad.net/rharding/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Please help me in solving this problem.. 

Regards,
Varun Bhat

---

### Post by Partyboi2 on 2008-12-28
You can disable that repo in Software Sources (System>Admin>Software Sources) Looks like there is no intrepid repo available from [http://ppa.launchpad.net/rharding](http://ppa.launchpad.net/rharding) only feisty, gusty and hardy.

---

### Post by balaknair on 2008-12-28
Yep, do as partyboi2 said. [http://ppa.launchpad.net/rharding](http://ppa.launchpad.net/rharding) doesn't have repositories for Intrepid. 

System menu> Administration> Software Sources--> Third Party Software--> Find the entries for [http://ppa.launchpad.net/rharding](http://ppa.launchpad.net/rharding) and remove the tick mark next to them.
Then Click 'Close'--> You will be asked if you want to reload the package lists, click 'Reload'.

That's it, you're done.

If this solves your problem, don't forget to thank Partyboi(click on the little medal icon at the lower right corner of his post) and mark the thread as 'Solved'(At the top of the thread on the right side, Thread tools> Mark as solved)

---

